---
title: "Závažná chyba C1091 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1091
dev_langs: C++
helpviewer_keywords: C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e9d5e9ba75457d89223ab187c1249cc73419fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1091"></a>Závažná chyba C1091
omezení kompilátoru: řetězec překračuje délku bajtů 'délka.  
  
 Řetězcová konstanta překročil aktuální limit délky řetězce.  
  
 Můžete chtít rozdělením statický řetězec proměnné dva (nebo více) a použít [strcpy_s –](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) připojení výsledek jako součást deklarace nebo při běhu.