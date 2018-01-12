---
title: "Spravované typy (C++-CL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __gc types
- types [C++], CLR
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9e7bbd9687c3cc696b35e0284d55a18f59c898cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="managed-types-ccl"></a>Spravované typy (C++/CL)
Syntaxe deklarace spravované typy a vytváření a používání objektů z těchto typů výrazně upravíte ze spravovaných rozšíření jazyka C++ na Visual C++. K tomu bylo potřeba k podpoře jejich integrace v rámci systém typů ISO C++. Tyto změny jsou podrobně uvedeny v následující témata.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Deklarace spravovaného typu třídy](../dotnet/declaration-of-a-managed-class-type.md)  
 Popisuje, jak deklarovat spravovanou `class`, `struct`, nebo `interface`.  
  
 [Deklarace objektu referenční třídy CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 Popisuje, jak deklarace objektu referenční třídy typu pomocí sledování popisovače.  
  
 [Deklarace pole CLR](../dotnet/declaration-of-a-clr-array.md)  
 Vysvětluje, jak deklarace a inicializace pole.  
  
 [Změny v pořadí inicializace konstruktoru](../dotnet/changes-in-constructor-initialization-order.md)  
 Popisuje klíčové změny v pořadí inicializace konstruktoru třídy.  
  
 [Změny v sémantice destruktorů](../dotnet/changes-in-destructor-semantics.md)  
 Popisuje nedeterministické dokončení `Finalize` versus `Dispose`, důsledky pro referenční objekty a použití explicitního `Finalize`.  
  
 **Poznámka:** diskuse o delegátech je odložena až do [Delegáti a události](../dotnet/delegates-and-events.md) s cílem je prezentovat se členy události v rámci třídy, obecné téma [deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI) ](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## <a name="see-also"></a>Viz také  
 [C + +/ CLI migrace Úvod do](../dotnet/cpp-cli-migration-primer.md)   
 [Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Pole](../windows/arrays-cpp-component-extensions.md)