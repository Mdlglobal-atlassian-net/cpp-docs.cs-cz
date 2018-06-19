---
title: Chyba linkerů Lnk2004 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2004
dev_langs:
- C++
helpviewer_keywords:
- LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2619ebc3fcf997574628354a951619cd18a81b46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314337"
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