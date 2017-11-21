---
title: "Upozornění nástroje BSCMAKE BK4504 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK4504
dev_langs: C++
helpviewer_keywords: BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7f6d854fbd74d9ca05ba6797bbd57db52b7a70e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504
soubor obsahuje příliš mnoho odkazů; ignoruje další odkazy z tohoto zdroje  
  
 Souboru obsahuje více než 64 000 odkazy na symboly. Když BSCMAKE došlo 64 000 odkazy v souboru, ignoruje všechny odkazy na další.  
  
 K odstranění problému, buď rozdělit na dvě nebo více souborů, z nichž každá má méně než 64 000 symbolů odkazy, nebo pomocí `#pragma component(browser)` preprocesoru směrnice pro symboly omezení, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [součást](../../preprocessor/component.md).