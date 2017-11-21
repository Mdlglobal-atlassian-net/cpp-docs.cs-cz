---
title: "C2338 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2338
dev_langs: C++
helpviewer_keywords: C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3b5f8773daa61b2ac7703b1ee0e5672818278e87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2338"></a>C2338 chyby kompilátoru  
  
> *Chybová zpráva*  
  
Tato chyba může být způsobeno `static_assert` došlo k chybě během kompilace. Zpráva poskytuje `static_assert` parametry.   
  
Tato chybová zpráva může být generována také externí zprostředkovatelé kompilátoru. Ve většině případů tyto chyby jsou hlášených poskytovatele atribut knihovny DLL, jako je například ATLPROV. Některé běžné formuláře této zprávy patří:

> '*atribut*' Atl atribut zprostředkovatele: Chyba ATL*číslo* *zpráv*  
  
> Nesprávné použití atributu '*atribut*.
  
> '*využití*': správný formát pro atribut 'využití.  
  
Tyto chyby jsou často neopravitelné a může následovat kompilátoru závažné chybě.  
  
Chcete-li tyto problémy vyřešit, opravte použití atributu. V některých případech, například musí být atribut parametry deklarován předtím, než mohou být použity. Pokud je k dispozici číslo ATL chyby, zkontrolujte v dokumentaci k této chybě podrobnější informace.  
