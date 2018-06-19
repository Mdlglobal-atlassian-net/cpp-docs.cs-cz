---
title: Změny u operátorů převodů | Microsoft Docs
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
ms.openlocfilehash: 750d16bc6fee86d8a3f8b912cdc4c251221dffb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110869"
---
# <a name="changes-to-conversion-operators"></a>Změny u operátorů převodů
Syntaxe pro operátory převodu změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Jedním z příkladů je zápis `op_Implicit` převodu. Zde je definice `MyDouble` provedených od specifikace jazyka:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 To uvádí, že zadané celé číslo, algoritmus pro převod tohoto celého čísla do `MyDouble` zajišťuje `op_Implicit` operátor. Kromě toho bude tento převod provést implicitně kompilátorem. Podobně dává `MyDouble` objektu, dva `op_Explicit` operátory poskytují příslušné algoritmy pro převod tohoto objektu na celé číslo nebo na spravovanou `String` entity. Kompilátor však nebude provádět převod, není-li explicitně požadované uživatelem.  
  
 V jazyce C# to vypadá takto:  
  
```  
class MyDouble {  
   public static implicit operator MyDouble( int i );   
   public static explicit operator int( MyDouble val );  
   public static explicit operator string( MyDouble val );   
};  
```  
  
 Kód jazyka C# vypadá jako C++ více než spravovaných rozšíření jazyka C++. To není případ v nové syntaxe.  
  
 ISO C++ představil klíčové slovo, `explicit`, ke zmírnění nežádoucích důsledků – například `Array` třída, která přebírá jednotlivý celočíselný argument jako dimenzi implicitně převede libovolné celé do `Array` objektu, který je, není to, co chcete. Je možné předejít návrhu stylu fiktivní druhý argumentu pro konstruktor  
  
 Na druhé straně byste neměli poskytnout pár převodu při navrhování typu třídy v rámci jazyka C++. Typickým příkladem pro tento je třída standardní řetězec. Implicitní převod je konstruktor jeden argument, který je přebírá řetězec stylu jazyka C. Však neposkytuje odpovídající implicitní převod operátor - převodu řetězec objekt na řetězec stylu jazyka C, ale spíše vyžaduje, aby uživatel explicitně vyvolat pojmenovanou funkci – v takovém případě `c_str()`.  
  
 Takže přidružení implicitního nebo explicitního chování na operátor převodu (a jako zapouzdření sady převodů do jediného formuláře deklarace) závisí na zlepšení podpory C++ pro operátory převodu, které případně vedly k `explicit` – klíčové slovo. Podporu jazyka Visual C++ pro operátory převodu vypadá takto, který je poněkud méně podrobná než u jazyka C# z důvodu výchozí chování operátoru podporující aplikaci implicitní převod algoritmu:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Další změnou je, že jediný argument konstruktoru je zpracováván jako kdyby je deklarován jako `explicit`. To znamená, že chcete-li aktivovat jeho volání, je vyžadována explicitní přetypování. Upozorňujeme však, že pokud je definována explicitní operátor převodu a není jeden argument konstruktoru, je vyvolána.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)