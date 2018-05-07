---
title: C2447 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2f0f72bc1278792853e1886e302f4410fdbe2d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2447"></a>C2447 chyby kompilátoru
{: chybějící hlavička funkce (formální seznam ve starém stylu)  
  
 Kompilátor narazil v globálním oboru na neočekávanou otevřenou složenou závorku. Ve většině případů je příčinou chybný formát hlavičky funkce, nesprávně umístěná deklarace nebo zapomenutý středník. Chcete-li tento problém vyřešit, ověřte, zda za otevřenou složenou závorkou následuje hlavička funkce se správným formátem, a zda před ní není deklarace nebo zapomenutý středník.  
  
 Tato chyba může být také způsobena seznamem formálních argumentů jazyka C ve starém stylu. Chcete-li tento problém vyřešit, přepište seznam argumentů tak, aby používal moderní styl, tedy byl uzavřený do závorek.  
  
 Následující ukázka generuje C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```