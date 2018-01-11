---
title: "Chyba linkerů Lnk2004 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2004
dev_langs: C++
helpviewer_keywords: LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fdbd32bbc59d9c18df5544f07ec7e7097b9e02e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2004"></a>Chyba linkerů LNK2004
přetečení relativní oprava GP ' cílit '; krátký ' sekce ' je příliš velký, nebo mimo rozsah.  
  
 V části byla příliš velká.  
  
 Pokud chcete tuto chybu vyřešit, zmenšete velikost oddílu krátké buď explicitně ukládání dat v částech dlouho prostřednictvím části #pragma (".sectionname", čtení, zápisu, long) a použitím `__declspec(allocate(".sectionname"))` na data definice a deklarace.  Například  
  
```  
#pragma section(".data$mylong", read, write, long)  
__declspec(allocate(".data$mylong"))  
char    rg0[1] = { 1 };  
char    rg1[2] = { 1 };  
char    rg2[4] = { 1 };  
char    rg3[8] = { 1 };  
char    rg4[16] = { 1 };  
char    rg5[32] = { 1 };  
```  
  
 Také můžete přesunout data logicky seskupeny do vlastní struktury, která bude kolekci dat, které jsou větší než 8 bajtů, které kompilátor přidělí dlouho datové části.  Například  
  
```  
// from this...  
int     w1  = 23;  
int     w2 = 46;  
int     w3 = 23*3;  
int     w4 = 23*4;  
  
// to this...  
struct X {  
    int     w1;  
    int     w2;  
    int     w3;  
    int     w4;  
} x  = { 23, 23*2, 23*3, 23*4 };  
  
```  
  
 Tato chyba je následován závažná chyba `LNK1165`.