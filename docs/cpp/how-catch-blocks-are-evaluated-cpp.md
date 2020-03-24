---
title: Postup vyhodnocení zachytávacího bloku (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 11804c48631659b84006abb824837efea3902416
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188634"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Postup vyhodnocení zachytávacího bloku (C++)

Jazyk C++ umožňuje vyvolat výjimky jakéhokoli typu, obecně je však doporučeno vyvolávat typy odvozené z typu std::exception. C++ Výjimka může být zachycena obslužnou rutinou **catch** , která určuje stejný typ jako vyvolaná výjimka, nebo obslužnou rutinou, která může zachytit jakýkoli typ výjimky.

Je-li typem vyvolané výjimky třída, která má také základní třídu (nebo třídy), lze ji zachytit obslužnými rutinami přijímajícími základní třídy i reference na základy daného typu výjimky. Povšimněte si, že je-li výjimka zachycena referencí, je svázána se skutečným objektem vyvolané výjimky. V ostatních případech jde o kopii (obdobně jako argument funkce).

Je-li vyvolána výjimka, může být zachycena následujícími typy obslužných rutin **catch** :

- Obslužná rutina, která může přijmout libovolný typ (pomocí syntaxe tří teček).

- Obslužná rutina, která přijímá stejný typ jako objekt výjimky; vzhledem k tomu, že se jedná o kopii, ignorují se modifikátory **const** a **volatile** .

- Obslužná rutina přijímající reference na typ shodný s objektem výjimky.

- Obslužná rutina, která přijímá odkaz na **konstantní** nebo **nestálou** formu stejného typu jako objekt výjimky.

- Obslužná rutina, která přijímá základní třídu stejného typu jako objekt výjimky; vzhledem k tomu, že se jedná o kopii, ignorují se modifikátory **const** a **volatile** . Obslužná rutina **catch** pro základní třídu nesmí předcházet obslužné rutině **catch** pro odvozenou třídu.

- Obslužná rutina přijímající referenci na základní třídu typu shodného s objektem výjimky.

- Obslužná rutina, která přijímá odkaz na **konstantu** nebo **nestálou** formu základní třídy stejného typu jako objekt výjimky.

- Obslužná rutina přijímající ukazatel, na nějž lze vyvolaný objekt ukazatele převést dle standardních pravidel pro převod ukazatelů.

Pořadí, ve kterém jsou obslužné rutiny **catch** významné, je důležité, protože obslužné rutiny pro daný blok **Try** jsou zkontrolovány v pořadí podle jejich vzhledu. Chybou je například umístit obslužnou rutinu základní třídy před obslužnou rutinu odvozené třídy. Po nalezení vyhovující obslužné rutiny **catch** nebudou další obslužné rutiny zkontrolovány. V důsledku toho musí být obslužná rutina **catch** se třemi tečkami poslední obslužnou rutinou pro svůj blok **Try** . Příklad:

```cpp
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

V tomto příkladu je obslužná rutina **catch** se třemi tečkami jedinou zkoušenou obslužnou rutinou.

## <a name="see-also"></a>Viz také

[Moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md)
