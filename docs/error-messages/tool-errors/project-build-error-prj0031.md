---
title: "Chyba sestavení projektu PRJ0031 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0031
dev_langs: C++
helpviewer_keywords: PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5aafec3bb4213ec8785cb6f05e0cc5e2ecc72e4a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0031"></a>Chyba sestavení projektu PRJ0031
Vlastnost 'výstupy, pro vlastní sestavovací krok pro 'file' obsažené 'Makro souboru, který vyhodnocuje se na 'macro_expansion'.  
  
 Vlastní krok sestavení na soubor měl chybný výstup pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamená, že je cesta chybně vytvořen, a to obsahující znaky, nebo kombinace znaků, které jsou neplatné v cestě k souboru.  
  
 Pokud chcete tuto chybu vyřešit, opravte makro nebo odstraňte specifikace cesty. Vyhodnotí cesta je absolutní cestu z adresáře projektu.