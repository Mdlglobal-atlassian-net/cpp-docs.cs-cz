---
title: "Upozornění nástroje BSCMAKE BK4504 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58a59b3141a8d7051aa7ece1bcb71dd960fabb18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504
soubor obsahuje příliš mnoho odkazů; ignoruje další odkazy z tohoto zdroje  
  
 Souboru obsahuje více než 64 000 odkazy na symboly. Když BSCMAKE došlo 64 000 odkazy v souboru, ignoruje všechny odkazy na další.  
  
 K odstranění problému, buď rozdělit na dvě nebo více souborů, z nichž každá má méně než 64 000 symbolů odkazy, nebo pomocí `#pragma component(browser)` preprocesoru směrnice pro symboly omezení, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [součást](../../preprocessor/component.md).