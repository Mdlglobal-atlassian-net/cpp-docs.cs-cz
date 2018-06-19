---
title: C2338 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156074f20517c1d2e2f4fdb4ac5c54d6cf014276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222303"
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
