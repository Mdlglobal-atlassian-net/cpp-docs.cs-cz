---
title: "C2803 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2803
dev_langs: C++
helpviewer_keywords: C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: efa9efa2dc204d302f69d873c0199d4431efccb1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2803"></a>C2803 chyby kompilátoru
'operátor operátor' musí mít alespoň jeden formální parametr typu třídy  
  
 Přetížené operátor chybí parametr typu třídy.  
  
 Je třeba předat minimálně jeden parametr odkazem (není pomocí ukazatele, ale odkazů) nebo hodnota, která má být schopni zapisovat "< b" (třídy typu A a b).  
  
 Pokud jsou oba parametry ukazatele bude čistý porovnání ukazatel adresy a nebude používat převod definovaný uživatelem.  
  
 Následující ukázka generuje C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```