---
title: "Závažná chyba C1081 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1081
dev_langs: C++
helpviewer_keywords: C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 148e3e6035304eb155a478e5971defd9a0a55120
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1081"></a>Závažná chyba C1081
'symbol': název souboru je příliš dlouhý  
  
 Délka názvu cesty souboru překračuje `_MAX_PATH` (definovanou STDLIB.h jako 260 znaků). Zkraťte název souboru.  
  
 Když zavoláte CL.exe s krátký název souboru, kompilátor možná muset vygenerovat úplnou cestu. Například `cl -c myfile.cpp` může způsobit, že kompilátor generuje:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```