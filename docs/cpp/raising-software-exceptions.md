---
title: Vyvolávání výjimek softwaru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75f882fe924ba825a5f3ec641a98175104635e92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085810"
---
# <a name="raising-software-exceptions"></a>Vyvolávání výjimek softwaru

Některé nejběžnější zdroje chyb programu nejsou systémem označeny jako výjimky. Například při pokusu o přidělení bloku paměti při nedostatku paměti nevyvolá funkce API nebo modul runtime výjimku, ale vrátí kód chyby.

Jakoukoli podmínku je však můžete považovat za výjimku nalezením této podmínky v kódu a následným nahlášením pomocí volání [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) funkce. Označením chyb tímto způsobem lze docílit výhod strukturovaného zpracování výjimek pro jakoukoli chybu modulu runtime.

Použití strukturovaného zpracování výjimek s chybami:

- Definujte vlastní kód výjimky pro událost.

- Volání `RaiseException` při zjištění problému.

- Pro otestování definovaného kódu výjimky použijte filtry zpracování výjimek.

\<Winerror.h > soubor zobrazuje formát kódů výjimek. Abyste se ujistili, že není definován kód, který je v rozporu s existujícím kódem výjimky, nastavte třetí nejvýznamnější bit na hodnotu 1. Čtyři nejvýznamnější bity je třeba nastavit tak, jak je znázorněno v následující tabulce.

|Bity|Doporučené binární nastavení|Popis|
|----------|--------------------------------|-----------------|
|31-30|11|Tyto dva bity popisují základní stav kódu: 11 = chyba, 00 = úspěch, 01 = informace, 10 = upozornění.|
|29|1|Klientský bit. Pro kódy definované uživatelem jej nastavte na hodnotu 1.|
|28|0|Vyhrazený bit. (Ponechejte nastavený na hodnotu 0.)|

Pokud je třeba, je možné nastavit první dva bity na nastavení jiné než binární 11. Nastavení „chyba“ je však vhodné pro většinu výjimek. Je důležité provést nastavení bitů 29 a 28, jak je uvedeno v předchozí tabulce.

Výsledný kód chyby by proto měl mít nejvyšší čtyři bity nastaveny na šestnáctkovou hodnotu E. Následující definice například definuje kódy výjimek, které nejsou v rozporu s žádné kódy výjimek pro Windows. (Bude však možná zapotřebí zkontrolovat, které kódy jsou používány knihovnami DLL třetích stran.)

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Po definování kódu výjimky jej lze použít pro vyvolání výjimky. Například následující kód vyvolá `STATUS_INSUFFICIENT_MEM` výjimky v reakci na problém s přidělováním paměti:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Pokud je zapotřebí jednoduše vyvolat výjimku, můžete nastavit poslední tři parametry na hodnotu 0. Poslední tři parametry jsou užitečné pro předávání dalších informací a pro nastavení příznaku, který zabrání obslužným rutinám pokračovat v provádění. Zobrazit [RaiseException](https://msdn.microsoft.com/library/windows/desktop/ms680552) funkce v sadě Windows SDK pro další informace.

V rámci filtrů zpracování výjimek lze následně otestovat definované kódy. Příklad:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)