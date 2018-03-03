---
title: "Chyba sestavení projektu PRJ0032 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0032
dev_langs:
- C++
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92497027db3a2449914696f03fc86a144a48b62e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0032"></a>Chyba sestavení projektu PRJ0032
Vlastnost 'Výstupy' pro úrovni projektu vlastní krok sestavení obsahovala 'Makro', který je vyhodnocen 'macro_expansion'.  
  
 Vlastní krok sestavení na projektu měl chybný výstup pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamená, že je cesta chybně vytvořen, a to obsahující znaky, nebo kombinace znaků, které jsou neplatné v cestě k souboru.  
  
 Pokud chcete tuto chybu vyřešit, opravte makro nebo odstraňte specifikace cesty. Vyhodnotí cesta je absolutní cestu z adresáře projektu.