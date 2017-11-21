---
title: Funkce Call (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0faf339877b075a1337c73ec5ca3c41a869ceec2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="function-call-c"></a>Volání funkcí (C)
„Volání funkce“ je výraz, který obsahuje název volané funkce nebo hodnotu ukazatele na funkci a volitelně také argumenty funkci předané.  
  
## <a name="syntax"></a>Syntaxe  
 *operátory výraz*:  
 *operátory výraz***(***seznam argumentů výraz* opt**)**   
  
 *Seznam argumentů výraz*:  
 *přiřazení – výraz*  
  
 *Seznam argumentů výraz***,***přiřazení – výraz*   
  
 *Operátory výraz* adresu funkce (například identifikátor funkce nebo hodnota ukazatel na funkci), se musí vyhodnotit a *seznam argumentů výraz* je seznam výrazů (oddělené čárkami) jejichž hodnoty ("argumenty") jsou předaný funkci. *Seznam argumentů výraz* argument nesmí být prázdné.  
  
 Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Viz [volání funkce](../c-language/function-calls.md) Další informace.)  
  
## <a name="see-also"></a>Viz také  
 [Operátor volání funkce:)](../cpp/function-call-operator-parens.md)