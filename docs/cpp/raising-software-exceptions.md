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
ms.openlocfilehash: d6e1ea4abadc3b751b8bad9f9521462d510c5227
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947677"
---
# <a name="raising-software-exceptions"></a>Vyvolávání výjimek softwaru
Některé nejběžnější zdroje chyb programu nejsou systémem označeny jako výjimky. Například při pokusu o přidělení bloku paměti při nedostatku paměti nevyvolá funkce API nebo modul runtime výjimku, ale vrátí kód chyby.  
  
 Jakoukoli podmínku je však můžete považovat za výjimku nalezením této podmínky v kódu a následným nahlášením pomocí volání [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) funkce. Označením chyb tímto způsobem lze docílit výhod strukturovaného zpracování výjimek pro jakoukoli chybu modulu runtime.  
  
 Použití strukturovaného zpracování výjimek s chybami:  
  
-   Definujte vlastní kód výjimky pro událost.  
  
-   Volání `RaiseException` při zjištění problému.  
  
-   Pro otestování definovaného kódu výjimky použijte filtry zpracování výjimek.  
  
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
  
 Po definování kódu výjimky jej lze použít pro vyvolání výjimky. Následující kód například vyvolá výjimku STATUS_INSUFFICIENT_MEM jako reakci na problém s přidělováním paměti:  
  
```cpp 
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 Pokud je zapotřebí jednoduše vyvolat výjimku, můžete nastavit poslední tři parametry na hodnotu 0. Poslední tři parametry jsou užitečné pro předávání dalších informací a pro nastavení příznaku, který zabrání obslužným rutinám pokračovat v provádění. Najdete v článku [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) fungovat v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] Další informace.  
  
 V rámci filtrů zpracování výjimek lze následně otestovat definované kódy. Příklad:  
  
```cpp 
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)