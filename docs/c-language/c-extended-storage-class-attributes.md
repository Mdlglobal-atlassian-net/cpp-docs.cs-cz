---
title: "Rozšířené atributy třídy úložiště jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C]
- extended attributes
- extended storage-class attributes
- storage class specifiers, C storage classes
ms.assetid: 2580735c-f5bf-46ab-9468-0696893d82be
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 119de1e705a0e3de93aadc61d38ecdde2fc43fe9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-extended-storage-class-attributes"></a>Rozšířené atributy třídy úložiště jazyka C
**Konkrétní Microsoft**  
  
 Více aktuální informace v tomto tématu najdete v části [__declspec (C++ – referenční informace)](../cpp/declspec.md).  
  
 Rozšířená syntaxe atributu zjednodušuje a standardizuje rozšíření specifické pro společnost Microsoft v rámci jazyka C. Mezi atributy třídy úložiště používající rozšířenou syntaxi atributů patří atributy thread, naked, dllimport a dllexport.  
  
 Rozšířená syntaxe atributů pro určení informací o třídě úložiště používá klíčové slovo __declspec, které určuje, že se instance daného typu uloží do níže uvedeného atributu třídy úložiště specifické pro společnost Microsoft (thread, naked, dllimport nebo dllexport). Příklady dalších modifikátorů tříd úložišť mohou být klíčová slova static a extern. Tato klíčová slova jsou však součástí standardu ANSI C a jako taková nejsou součástí rozšířené syntaxe atributů.  
  
## <a name="syntax"></a>Syntaxe  
 *specifikátor třídy úložiště*:  
 `__declspec`( *rozšířené decl – modifikátor seq* ) / * specifické pro Microsoft\*/  
  
 *Rozšířené decl – modifikátor seq*:  
 *Rozšířené modifikátor decl* opt  
  
 *Rozšířené rozšířené decl – modifikátor seq – decl – modifikátor*  
  
 *Rozšířené modifikátor decl*:  
 **přístup z více vláken**  
  
 **holé**  
  
 **DllImport**  
  
 `dllexport`  
  
 Modifikátory deklarace jsou odděleny prázdným znakem. Všimněte si, že *rozšířené decl – modifikátor seq* nesmí být prázdné; v takovém případě __declspec nemá žádný vliv.  
  
 Atributy třídy úložiště thread, naked, dllimport a dllexport jsou vlastnostmi pouze té deklarace dat nebo funkce, pro kterou jsou použity. Tyto atributy nemění definice atributů typů samotné funkce. Atribut thread ovlivňuje pouze data. Atribut naked ovlivňuje pouze funkce. Atributy dllimport a dllexport ovlivňují funkce i data.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)