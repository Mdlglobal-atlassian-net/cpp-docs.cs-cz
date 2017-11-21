---
title: "Vyvolávání výjimek softwaru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b19503d60629011621ef320b46325e17a217804c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="raising-software-exceptions"></a>Vyvolávání výjimek softwaru
Některé nejběžnější zdroje chyb programu nejsou systémem označeny jako výjimky. Například při pokusu o přidělení bloku paměti při nedostatku paměti nevyvolá funkce API nebo modul runtime výjimku, ale vrátí kód chyby.  
  
 Však lze považovat všechny podmínky jako výjimku zjišťuje tuto podmínku ve vašem kódu a pak ho reporting voláním [raiseexception –](http://msdn.microsoft.com/library/windows/desktop/ms680552) funkce. Označením chyb tímto způsobem lze docílit výhod strukturovaného zpracování výjimek pro jakoukoli chybu modulu runtime.  
  
 Použití strukturovaného zpracování výjimek s chybami:  
  
-   Definujte vlastní kód výjimky pro událost.  
  
-   Volání **raiseexception –** při zjištění problém.  
  
-   Pro otestování definovaného kódu výjimky použijte filtry zpracování výjimek.  
  
 Soubor WINERROR.H zobrazuje formát kódů výjimek. Abyste se ujistili, že není definován kód, který je v rozporu s existujícím kódem výjimky, nastavte třetí nejvýznamnější bit na hodnotu 1. Čtyři nejvýznamnější bity je třeba nastavit tak, jak je znázorněno v následující tabulce.  
  
|Bity|Doporučené binární nastavení|Popis|  
|----------|--------------------------------|-----------------|  
|31-30|11|Tyto dva bity popisují základní stav kódu: 11 = chyba, 00 = úspěch, 01 = informace, 10 = upozornění.|  
|29|1|Klientský bit. Pro kódy definované uživatelem jej nastavte na hodnotu 1.|  
|28|0|Vyhrazený bit. (Ponechejte nastavený na hodnotu 0.)|  
  
 Pokud je třeba, je možné nastavit první dva bity na nastavení jiné než binární 11. Nastavení „chyba“ je však vhodné pro většinu výjimek. Je důležité provést nastavení bitů 29 a 28, jak je uvedeno v předchozí tabulce.  
  
 Výsledný kód chyby proto by měl mít nejvyšší sadu hexadecimální E. čtyři bitů Můžete například definovat následující definice kódy výjimek, které nejsou v konfliktu s žádné kódy pro Windows výjimky. (Bude však možná zapotřebí zkontrolovat, které kódy jsou používány knihovnami DLL třetích stran.)  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 Po definování kódu výjimky jej lze použít pro vyvolání výjimky. Následující kód například vyvolá výjimku STATUS_INSUFFICIENT_MEM jako reakci na problém s přidělováním paměti:  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 Pokud je zapotřebí jednoduše vyvolat výjimku, můžete nastavit poslední tři parametry na hodnotu 0. Poslední tři parametry jsou užitečné pro předávání dalších informací a pro nastavení příznaku, který zabrání obslužným rutinám pokračovat v provádění. Najdete v článku [raiseexception –](http://msdn.microsoft.com/library/windows/desktop/ms680552) v fungovat [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] Další informace.  
  
 V rámci filtrů zpracování výjimek lze následně otestovat definované kódy. Příklad:  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis obslužné rutiny výjimek](../cpp/writing-an-exception-handler.md)   
 [Strukturované zpracování (C/C++) výjimek](../cpp/structured-exception-handling-c-cpp.md)