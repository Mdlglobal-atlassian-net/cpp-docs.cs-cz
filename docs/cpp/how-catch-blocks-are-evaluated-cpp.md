---
title: Jak zachytávacího bloku jsou vyhodnocení (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6343abec7e80bcbc47595856e6fd71a3e204ed54
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Postup vyhodnocení zachytávacího bloku (C++)
Jazyk C++ umožňuje vyvolat výjimky jakéhokoli typu, obecně je však doporučeno vyvolávat typy odvozené z typu std::exception. Může být zachycena výjimka C++ **catch** obslužná rutina, která určuje stejného typu jako vyvolaná výjimka nebo obslužná rutina, která může zachytit jakýkoli typ výjimky.  
  
 Je-li typem vyvolané výjimky třída, která má také základní třídu (nebo třídy), lze ji zachytit obslužnými rutinami přijímajícími základní třídy i reference na základy daného typu výjimky. Povšimněte si, že je-li výjimka zachycena referencí, je svázána se skutečným objektem vyvolané výjimky. V ostatních případech jde o kopii (obdobně jako argument funkce).  
  
 Pokud je vyvolána výjimka, může být zachycena následující typy **catch** obslužné rutiny:  
  
-   Obslužná rutina, která může přijmout libovolný typ (pomocí syntaxe tří teček).  
  
-   Obslužná rutina, která přijímá stejného typu jako objekt výjimky; protože se jedná o kopii, **const** a `volatile` modifikátory jsou ignorovány.  
  
-   Obslužná rutina přijímající reference na typ shodný s objektem výjimky.  
  
-   Obslužná rutina, která přijímá odkaz na **const** nebo `volatile` formuláře stejného typu jako objekt výjimky.  
  
-   Obslužná rutina, která přijímá základní třídu stejného typu jako objekt výjimky; vzhledem k tomu, že je kopie, **const** a `volatile` modifikátory jsou ignorovány. **Catch** nesmí předcházet obslužné rutiny pro základní třídu **catch** obslužné rutiny pro odvozené třídy.  
  
-   Obslužná rutina přijímající referenci na základní třídu typu shodného s objektem výjimky.  
  
-   Obslužná rutina, která přijímá odkaz na **const** nebo `volatile` formuláři základní třída stejného typu jako objekt výjimky.  
  
-   Obslužná rutina přijímající ukazatel, na nějž lze vyvolaný objekt ukazatele převést dle standardních pravidel pro převod ukazatelů.  
  
 Pořadí, v jakém **catch** obslužné rutiny zobrazí, je důležité, protože obslužné rutiny pro danou **zkuste** bloku se zkontrolují v pořadí podle jejich vzhled. Chybou je například umístit obslužnou rutinu základní třídy před obslužnou rutinu odvozené třídy. Po odpovídající **catch** nenajde obslužná rutina, nejsou zkontrolován následné obslužné rutiny. V důsledku toho, třemi tečkami **catch** obslužné rutiny musí být poslední obslužné rutiny pro jeho **zkuste** bloku. Příklad:  
  
```  
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 V tomto příkladu se třemi tečkami **catch** obslužná rutina je pouze obslužná rutina, která je zkontrolován.  
  
## <a name="see-also"></a>Viz také  
 [Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)