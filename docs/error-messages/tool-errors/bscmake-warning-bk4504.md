---
title: Upozornění nástroje BSCMAKE BK4504 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a17aa8b4e2a98d3bda5d21ea84962791b8051dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504
soubor obsahuje příliš mnoho odkazů; ignoruje další odkazy z tohoto zdroje  
  
 Souboru obsahuje více než 64 000 odkazy na symboly. Když BSCMAKE došlo 64 000 odkazy v souboru, ignoruje všechny odkazy na další.  
  
 K odstranění problému, buď rozdělit na dvě nebo více souborů, z nichž každá má méně než 64 000 symbolů odkazy, nebo pomocí `#pragma component(browser)` preprocesoru směrnice pro symboly omezení, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [součást](../../preprocessor/component.md).