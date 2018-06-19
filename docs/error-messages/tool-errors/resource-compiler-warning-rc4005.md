---
title: Upozornění kompilátoru prostředků RC4005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 724764e443d4ab999c1df1247e9f5572ebdb2078
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322481"
---
# <a name="resource-compiler-warning-rc4005"></a>Upozornění kompilátoru prostředků RC4005
"identifikátor": předefinování – makro  
  
 Identifikátor je definována dvakrát. Kompilátor použít druhý definici makra.  
  
 Toto upozornění může být způsobeno definice makra na příkazovém řádku a v kódu s `#define` – direktiva. Je také může být způsobeno makra naimportované z zahrnout soubory.  
  
 Pokud chcete odstranit toto upozornění, buď odeberte jeden z definice nebo použijte `#undef` direktivy před definici druhý.