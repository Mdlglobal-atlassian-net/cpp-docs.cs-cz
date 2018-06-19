---
title: Závažná chyba C1081 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b5ea18ff3f2714d9621d4372cf541be2f9b225a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33230519"
---
# <a name="fatal-error-c1081"></a>Závažná chyba C1081
'symbol': název souboru je příliš dlouhý  
  
 Délka názvu cesty souboru překračuje `_MAX_PATH` (definovanou STDLIB.h jako 260 znaků). Zkraťte název souboru.  
  
 Když zavoláte CL.exe s krátký název souboru, kompilátor možná muset vygenerovat úplnou cestu. Například `cl -c myfile.cpp` může způsobit, že kompilátor generuje:  
  
```  
D:\<very-long-directory-path>\myfile.cpp  
```