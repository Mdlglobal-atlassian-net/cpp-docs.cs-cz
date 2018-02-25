---
title: "#ifdef – a #ifndef – direktivy (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8f1a10e9d8437b71591efc9ce2915c9f485e0c4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef a #ifndef – direktivy (C/C++)
**#Ifdef** a **#ifndef** direktivy provést stejný úkol jako `#if` – direktiva při použití s **definované**( *identifikátor* ).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít **#ifdef** a **#ifndef** direktivy kdekoli `#if` lze použít. **#Ifdef** *identifikátor* je ekvivalentní příkaz `#if 1` při *identifikátor* byla definována, a je ekvivalentní `#if 0` při *identifikátor* nebyl definován nebo není byla definována s `#undef` – direktiva. Tyto direktivy pouze kontrole přítomnosti nebo absenci identifikátory definován s `#define`, ne pro identifikátory deklarován ve zdrojovém kódu jazyka C nebo C++.  
  
 Tyto direktivy jsou poskytovány pouze pro kompatibilitu s předchozími verzemi jazyka. **Definované (** *identifikátor* **)** konstantní výraz použít s `#if` – direktiva je upřednostňovaný.  
  
 **#Ifndef** – direktiva vyhledává opak podmínka kontrolovat pomocí **#ifdef**. Pokud nebyl definován identifikátor (nebo její definice byl odebrán s `#undef`), podmínka hodnotu true (nenulové hodnoty). Jinak je podmínka vyhodnocena jako false (0).  
  
 **Microsoft Specific**  
  
 *Identifikátor* mohou být předány z příkazového řádku pomocí možnosti /D. Až 30 makra lze zadat s /D.  
  
 To je užitečné pro kontrolu, jestli existuje definice, protože definice mohou být předány z příkazového řádku. Příklad:  
  
```  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)