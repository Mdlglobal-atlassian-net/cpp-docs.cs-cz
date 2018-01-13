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
ms.workload: cplusplus
ms.openlocfilehash: 8f27de973f0ff18493c182bdf1feb3f2812f39af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005
"identifikátor": předefinování – makro  
  
 Identifikátor je definována dvakrát. Kompilátor použít druhý definici makra.  
  
 Toto upozornění může být způsobeno definice makra na příkazovém řádku a v kódu s `#define` – direktiva. Je také může být způsobeno makra naimportované z zahrnout soubory.  
  
 Pokud chcete odstranit toto upozornění, buď odeberte jeden z definice nebo použijte `#undef` direktivy před definici druhý.