---
title: "Závažná chyba nástroje NMAKE U1100 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1100
dev_langs: C++
helpviewer_keywords: U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b489c1276b62e28fd540df369a84835c98da87e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1100"></a>Závažná chyba nástroje NMAKE U1100
Makro 'Makro' není povolen v kontextu batch pravidlo 'rule'  
  
 NMAKE generuje tato chyba, pokud blok příkazu pravidla dávkového režimu přímo nebo nepřímo odkazuje na makro speciální soubor, který není $<.  
  
 $< je jediným povoleno makro pro pravidla dávkového režimu.