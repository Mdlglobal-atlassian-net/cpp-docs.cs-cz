---
title: "Závažná chyba C1014 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1014
dev_langs: C++
helpviewer_keywords: C1014
ms.assetid: 4c01ef70-e765-4d07-a3fe-a11c19fb610b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bc5e4a5e316af927bbfd5d1d78ac90fe29e6a6fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1014"></a>Závažná chyba C1014
příliš mnoho souborů patří: hloubka = úroveň  
  
 Vnořené `#include` direktivy je příliš hluboké. Vnořené direktivy může zahrnovat otevřených souborů. Zdrojový soubor obsahující direktivu počítá jako jeden soubor.