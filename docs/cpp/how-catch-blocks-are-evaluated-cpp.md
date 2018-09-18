---
title: Jak zachytávacího bloku vyhodnocení (C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: fe86770692554551b88e1aef9bbddc509e21f0f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039436"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Postup vyhodnocení zachytávacího bloku (C++)

Jazyk C++ umožňuje vyvolat výjimky jakéhokoli typu, obecně je však doporučeno vyvolávat typy odvozené z typu std::exception. Výjimky jazyka C++ lze zachytit **catch** obslužná rutina, která určuje typ shodný s vyvolanou výjimkou, nebo obslužnou rutinu, která zachycuje všechny typy výjimek.

Je-li typem vyvolané výjimky třída, která má také základní třídu (nebo třídy), lze ji zachytit obslužnými rutinami přijímajícími základní třídy i reference na základy daného typu výjimky. Povšimněte si, že je-li výjimka zachycena referencí, je svázána se skutečným objektem vyvolané výjimky. V ostatních případech jde o kopii (obdobně jako argument funkce).

Když je vyvolána výjimka, lze ji zachytit následujícími typy z **catch** obslužné rutiny:

- Obslužná rutina, která může přijmout libovolný typ (pomocí syntaxe tří teček).

- Obslužná rutina přijímající stejného typu jako objektem výjimky. protože se jedná o kopii, **const** a **volatile** modifikátory jsou ignorovány.

- Obslužná rutina přijímající reference na typ shodný s objektem výjimky.

- Obslužná rutina přijímající referenci **const** nebo **volatile** formu stejného typu jako objekt výjimky.

- Obslužná rutina přijímající základní třídu stejného typu jako objektem výjimky. protože se jedná o kopii, **const** a **volatile** modifikátory jsou ignorovány. **Catch** nesmí předcházet obslužnou rutinu pro základní třídu **catch** obslužnou rutinu odvozené třídy.

- Obslužná rutina přijímající referenci na základní třídu typu shodného s objektem výjimky.

- Obslužná rutina přijímající referenci **const** nebo **volatile** formuláře základní třídy stejného typu jako objekt výjimky.

- Obslužná rutina přijímající ukazatel, na nějž lze vyvolaný objekt ukazatele převést dle standardních pravidel pro převod ukazatelů.

Pořadí, ve kterém **catch** obslužné rutiny se zobrazí, je důležité, protože obslužné rutiny pro danou **zkuste** bloku jsou zkoumány podle pořadí jejich výskytu. Chybou je například umístit obslužnou rutinu základní třídy před obslužnou rutinu odvozené třídy. Po nalezení odpovídající **catch** obslužná rutina se nachází, není prozkoumán další obslužné rutiny. V důsledku toho trojtečka **catch** obslužná rutina musí být poslední obslužnou rutinou pro jeho **zkuste** bloku. Příklad:

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

V tomto příkladu se třemi tečkami **catch** obslužná rutina je jedinou vyšetřenou obslužnou rutinou.

## <a name="see-also"></a>Viz také:

[Zpracovávání výjimek v jazyce C++](../cpp/cpp-exception-handling.md)