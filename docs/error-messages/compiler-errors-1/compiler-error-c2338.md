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
ms.workload: cplusplus
ms.openlocfilehash: e0171654bde5b056a7e6695ea5fbbe84edb62f83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
