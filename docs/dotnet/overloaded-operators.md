---
title: Přetížené operátory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- operator overloading, in a CLR class
- operators [C++], overloading
ms.assetid: 30391426-afe7-4497-bf22-e4816c1e48c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a53b8df6f10a4fb8efcd91ce5d9c3f0125320139
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425857"
---
# <a name="overloaded-operators"></a>Přetížené operátory

Přetížení operátoru významně změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

V deklaraci typu odkazu pro příklad, nikoli pomocí nativní `operator+` syntaxi, je explicitně vypsat interní název operátoru – v takovém případě `op_Addition`. Kromě toho musí explicitně vyvolat pomocí tohoto názvu, vylučuje dvě hlavní výhody přetížení operátoru volání operátoru: (a) intuitivní syntaxi a (b) je schopnost kombinovat nových typů pomocí existujících typů. Příklad:

```
public __gc __sealed class Vector {
public:
   Vector( double x, double y, double z );

   static bool    op_Equality( const Vector*, const Vector* );
   static Vector* op_Division( const Vector*, double );
   static Vector* op_Addition( const Vector*, const Vector* );
   static Vector* op_Subtraction( const Vector*, const Vector* );
};

int main()
{
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );

   Vector *pc1 = Vector::op_Addition( pa, pb );
   Vector *pc2 = Vector::op_Subtraction( pa, pc1 );
   Vector *pc3 = Vector::op_Division( pc1, pc2->x );

   if ( Vector::op_Equality( pc1, pc2 ))
      ;
}
```

V nové syntaxi budou obnoveny obvykle očekávání nativní programátor C++, jak v deklaraci a použití statické operátorů. Tady je `Vector` třídy přeložit na novou syntaxi:

```
public ref class Vector sealed {
public:
   Vector( double x, double y, double z );

   static bool    operator ==( const Vector^, const Vector^ );
   static Vector^ operator /( const Vector^, double );
   static Vector^ operator +( const Vector^, const Vector^ );
   static Vector^ operator -( const Vector^, const Vector^ );
};

int main()
{
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );
   Vector^ pb = gcnew Vector( 1.475,4.8916,-1.23 );

   Vector^ pc1 = pa + pb;
   Vector^ pc2 = pa - pc1;
   Vector^ pc3 = pc1 / pc2->x;

   if ( pc1 == pc2 )
      ;
}
```

## <a name="see-also"></a>Viz také

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)