---
title: Deklarace indexu vlastnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76473ce04cdf5860476b7612ddcbf00b40a0fae1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="property-index-declaration"></a>Deklarace indexu vlastnosti
Syntaxe deklarace indexované vlastnosti změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Dvěma hlavními nedostatky spravovaných rozšíření jazyka podpoře indexované vlastnosti je neschopnost poskytovat předplatné úrovni třídy; To znamená, všechny indexované vlastnosti je potřeba mít název, a proto neexistuje žádný způsob, například k poskytování spravovaného operátor dolního indexu, který můžete použít přímo na `Vector` nebo `Matrix` objektu třídy. Druhý méně významným nedostatkem je, že je vizuálně obtížné rozlišit vlastnost z indexované vlastnosti – počet parametrů je jediné. Nakonec indexované vlastnosti trpí problémy stejné jako u jiných indexované vlastnosti – přístupy nejsou považovány za atomické jednotky, ale rozděleny do jednotlivých metod.  Příklad:  
  
```  
public __gc class Vector;  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value);  
   __property float get_Item( int r, int c );  
  
   __property void set_Row( int r, Vector* value );  
   __property Vector* get_Row( int r );  
};  
```  
  
 Jak můžete vidět zde, indexery, které jsou rozlišené pouze další parametry, zadejte dva nebo jeden index dimenze. V nové syntaxe indexery, které jsou rozlišené závorky ([],) za název indexeru a o tom, počet a typ každý index:  
  
```  
public ref class Vector {};  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 K označení úrovně indexeru třídy, který lze použít přímo na objekty třídy v nové syntaxe `default` – klíčové slovo se znovu použije k nahrazení pro explicitní název. Příklad:  
  
```  
public ref class Matrix {  
private:  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c );  
      void set( int r, int c, float value );  
   }  
  
   property Vector^ Row [int] {  
      Vector^ get( int r );  
      void set( int r, Vector^ value );  
   }  
};  
```  
  
 V nové syntaxe při indexované výchozí hodnota je zadána vlastnost, oba tyto názvy jsou vyhrazené: `get_Item` a `set_Item`. Je to proto, že toto jsou základní názvy generované Výchozí indexované vlastnosti.  
  
 Všimněte si, že je podobná jednoduché syntaxi vlastnosti jednoduchá index syntaxe.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 