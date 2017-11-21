---
title: "Upozornění kompilátoru prostředků RC4005 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC4005
dev_langs: C++
helpviewer_keywords: RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 44c7239ffc814c17966bf3777218d3f8d88c9996
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005
"identifikátor": předefinování – makro  
  
 Identifikátor je definována dvakrát. Kompilátor použít druhý definici makra.  
  
 Toto upozornění může být způsobeno definice makra na příkazovém řádku a v kódu s `#define` – direktiva. Je také může být způsobeno makra naimportované z zahrnout soubory.  
  
 Pokud chcete odstranit toto upozornění, buď odeberte jeden z definice nebo použijte `#undef` direktivy před definici druhý.