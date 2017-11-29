---
title: "Závažná chyba nástroje NMAKE U1070 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1070
dev_langs: C++
helpviewer_keywords: U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d1efb239043e86cfa2013aed86db264a68638419
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1070"></a>Závažná chyba nástroje NMAKE U1070
cyklus definice makra 'makra.  
  
 Definice daného makra obsahovala makro jehož definice obsažené dané makro. Definice maker cyklické jsou neplatné.  
  
## <a name="example"></a>Příklad  
 Následující definice maker  
  
```  
ONE=$(TWO)  
TWO=$(ONE)  
```  
  
 dojít k následující chybě:  
  
```  
cycle in macro definition 'TWO'  
```