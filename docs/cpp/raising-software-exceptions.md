---
title: Vyvolání výjimek softwaru
ms.date: 11/04/2016
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
ms.openlocfilehash: 7c58ae2e2b6635345a162d11d2b75a9865d37751
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246410"
---
# <a name="raising-software-exceptions"></a>Vyvolání výjimek softwaru

Některé nejběžnější zdroje chyb programu nejsou systémem označeny jako výjimky. Například při pokusu o přidělení bloku paměti při nedostatku paměti nevyvolá funkce API nebo modul runtime výjimku, ale vrátí kód chyby.

However, you can treat any condition as an exception by detecting that condition in your code and then reporting it by calling the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function. Označením chyb tímto způsobem lze docílit výhod strukturovaného zpracování výjimek pro jakoukoli chybu modulu runtime.

Použití strukturovaného zpracování výjimek s chybami:

- Definujte vlastní kód výjimky pro událost.

- Call `RaiseException` when you detect a problem.

- Pro otestování definovaného kódu výjimky použijte filtry zpracování výjimek.

The \<winerror.h> file shows the format for exception codes. Abyste se ujistili, že není definován kód, který je v rozporu s existujícím kódem výjimky, nastavte třetí nejvýznamnější bit na hodnotu 1. Čtyři nejvýznamnější bity je třeba nastavit tak, jak je znázorněno v následující tabulce.

|Bity|Doporučené binární nastavení|Popis|
|----------|--------------------------------|-----------------|
|31-30|11|Tyto dva bity popisují základní stav kódu: 11 = chyba, 00 = úspěch, 01 = informace, 10 = upozornění.|
|29|1|Klientský bit. Pro kódy definované uživatelem jej nastavte na hodnotu 1.|
|28|0|Vyhrazený bit. (Ponechejte nastavený na hodnotu 0.)|

Pokud je třeba, je možné nastavit první dva bity na nastavení jiné než binární 11. Nastavení „chyba“ je však vhodné pro většinu výjimek. Je důležité provést nastavení bitů 29 a 28, jak je uvedeno v předchozí tabulce.

The resulting error code should therefore have the highest four bits set to hexadecimal E. For example, the following definitions define exception codes that do not conflict with any Windows exception codes. (Bude však možná zapotřebí zkontrolovat, které kódy jsou používány knihovnami DLL třetích stran.)

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Po definování kódu výjimky jej lze použít pro vyvolání výjimky. For example, the following code raises the `STATUS_INSUFFICIENT_MEM` exception in response to a memory allocation problem:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Pokud je zapotřebí jednoduše vyvolat výjimku, můžete nastavit poslední tři parametry na hodnotu 0. Poslední tři parametry jsou užitečné pro předávání dalších informací a pro nastavení příznaku, který zabrání obslužným rutinám pokračovat v provádění. See the [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) function in the Windows SDK for more information.

V rámci filtrů zpracování výjimek lze následně otestovat definované kódy. Příklad:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Viz také:

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[Structured exception handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)