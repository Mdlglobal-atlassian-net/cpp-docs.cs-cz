---
title: Zkuste – s výjimkou Statement (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c55ff2599fac14be0be9ac852727167dd34e02d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391711"
---
# <a name="try-except-statement-c"></a>try-except – příkaz (C)
**Konkrétní Microsoft**  
  
 **Zkuste – s výjimkou** příkaz je rozšíření Microsoft pro jazyk C, která umožňuje aplikacím převzít kontrolu nad program, když dojde k události, které obvykle ukončí zpracování. Tyto události jsou nazývány výjimkami a mechanismus, který se výjimkami zabývá, se nazývá strukturované zpracování výjimek.  
  
 Výjimky může být buď hardwaru nebo softwaru – na základě. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.  
  
## <a name="syntax"></a>Syntaxe  
 *Zkuste s výjimkou příkaz*:  
 **__try***složené – příkaz*   
  
 **__except (***výraz***)***složené – příkaz*   
  
 Složený příkaz po `__try` části chráněného je klauzule. Složený příkaz po klauzuli `__except` je obslužnou rutinou výjimky. Obslužná rutina určuje sadu akcí, které mají být provedeny, pokud dojde k výjimce během zpracování oddílu chráněného. Provádění pokračuje následujícím způsobem:  
  
1.  Chráněná část je spuštěna.  
  
2.  Nedojde-li za běhu chráněné části k žádné výjimce, pokračuje běh programu příkazem za klauzulí `__except`.  
  
3.  Pokud dojde k výjimce během zpracování oddílu chráněného nebo v jakékoli rutině části chráněného volá, `__except` výraz vyhodnocen a hodnota vrácená Určuje, jak je výjimka ošetřena. Existují tři hodnoty:  
  
     `EXCEPTION_CONTINUE_SEARCH` Výjimka nebyla rozpoznána. Pokračovat ve vyhledávání nahoru v zásobníku pro obslužnou rutinu, nejdřív pro obsahující **zkuste – s výjimkou** příkazy, pak pro obslužné rutiny s další nejvyšší prioritou.  
  
     `EXCEPTION_CONTINUE_EXECUTION` Výjimka je rozpoznána ale vynechat. Program bude pokračovat tam, kde k výjimce došlo.  
  
     `EXCEPTION_EXECUTE_HANDLER` Výjimka je rozpoznat. Přenos řízení na obslužnou rutinu výjimky spuštěním `__except` složený příkaz a potom v provádění pokračovat v místě, se vyskytla výjimka.  
  
 Protože `__except` výraz vyhodnocen jako výraz C, je omezený na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárka. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.  
  
> [!NOTE]
>  Strukturované zpracování výjimek pracuje s C a C++ zdrojové soubory. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování mechanismus výjimek C++ je také mnohem víc možností, v tom, že ho můžete zpracování výjimek libovolného typu.  
  
> [!NOTE]
>  Pro C++ – programy je třeba použít zpracovávání výjimek v jazyce C++ místo strukturované zpracování výjimek. Další informace najdete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *referenční příručka jazyka C++*.  
  
 Každou rutinu v aplikaci může mít svůj vlastní obslužná rutina výjimky. `__except` Výraz spouští v rámci oboru `__try` textu. To znamená, že má přístup k žádné místní proměnné deklarovány existuje.  
  
 `__leave` – Klíčové slovo je platný v rámci **zkuste – s výjimkou** příkaz bloku. Účinek `__leave` je chcete přejít na konci **zkuste – s výjimkou** bloku. Provádění obnovení na konci obslužná rutina výjimky. I když `goto` příkaz lze použít k dosažení stejného výsledku `goto` příkaz způsobuje uvolnění zásobníku. `__leave` Příkaz je efektivnější, protože nezahrnuje uvolnění zásobníku.  
  
 Ukončení **zkuste – s výjimkou** příkaz pomocí `longjmp` běhové funkce považuje za abnormální ukončení. Není povolen přejít do `__try` prohlášení, ale právní přejít od jednoho. Obslužná rutina výjimky není volána, pokud je tento proces se ukončil uprostřed provádění **zkuste – s výjimkou** příkaz.  
  
## <a name="example"></a>Příklad  
 Tady je příklad obslužné rutiny výjimek a obslužné rutiny ukončení. V tématu [try-finally – příkaz](../c-language/try-finally-statement-c.md) Další informace o obslužné rutiny ukončení.  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 Toto je výstup s komentářem přidat na pravé straně příkladu:  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [try-except – příkaz](../cpp/try-except-statement.md)