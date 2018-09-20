---
title: Změny operátorů převodu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03b17c5abc559289a9f85a10b9c5914b49498922
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381104"
---
# <a name="changes-to-conversion-operators"></a>Změny u operátorů převodů

Syntaxe pro operátory převodu změnila ze spravovaného rozšíření jazyka C++ pro Visual C++.

Jedním z příkladů je napsat `op_Implicit` převodu. Tady je definicí `MyDouble` z specifikace jazyka:

```
__gc struct MyDouble {
   static MyDouble* op_Implicit( int i );
   static int op_Explicit( MyDouble* val );
   static String* op_Explicit( MyDouble* val );
};
```

To říká, celé číslo, algoritmus pro převod tohoto celé číslo na zadaný `MyDouble` je poskytován `op_Implicit` operátor. Kromě toho tento převod bude proveden implicitně kompilátorem. Podobně `MyDouble` objektu, dva `op_Explicit` operátory poskytnout příslušné algoritmy pro převod objektu na celé číslo nebo spravované `String` entity. Kompilátor však nebude převod provést, pokud explicitně požadavku uživatele.

V jazyce C# vypadá takto:

```
class MyDouble {
   public static implicit operator MyDouble( int i );
   public static explicit operator int( MyDouble val );
   public static explicit operator string( MyDouble val );
};
```

Kód jazyka C# vypadá jako C++ více než spravovaných rozšíření jazyka C++. To není případ v nové syntaxi.

ISO-C++ představil klíčového slova `explicit`, jak zmírnit nežádoucí důsledky – například `Array` třída, která přebírá jediný celočíselný argument jako dimenze implicitně převede libovolné celé číslo do `Array` objekt, který je, není to, co chcete. Jedním ze způsobů, aby k tomu je návrh idiomu fiktivní druhý argument pro konstruktor

Na druhé straně byste neměli poskytnout pár převodu při návrhu typu třídy v rámci jazyka C++. Nejlepším příkladem, který je standardní řetězcové třídy. Implicitní převod je jedním argumentem konstruktor, který přebírá řetězec C-style. Však neposkytuje odpovídající Operátor implicitního převodu - u převodu řetězce objekt na řetězec ve stylu jazyka C, ale místo toho vyžaduje, aby uživatel explicitně vyvolat pojmenované funkce – v takovém případě `c_str()`.

Ano přidružení implicitního/explicitního chování na operátor převodu (a jako zapouzdření sadu převody jediného formuláře deklarace) se zdá být vylepšení podpory C++ pro operátory převodu, což nakonec vedlo k `explicit` – klíčové slovo. Podpora jazyka Visual C++ pro operátory převodu vypadá takto, což je o něco méně podrobný než C# z důvodu výchozí chování operátoru podporuje implicitní aplikaci algoritmus převodu:

```
ref struct MyDouble {
public:
   static operator MyDouble^ ( int i );
   static explicit operator int ( MyDouble^ val );
   static explicit operator String^ ( MyDouble^ val );
};
```

Další změnou je, že jediný argument konstruktoru je zpracováván jako v případě, že je deklarována jako `explicit`. To znamená, že aby bylo možné aktivovat její volání, není vyžadováno explicitní přetypování. Všimněte si však, že pokud je definován explicitního operátoru převodu a ne konstruktoru jedním argumentem, je vyvolána.

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)