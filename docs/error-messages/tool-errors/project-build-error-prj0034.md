---
title: "Chyba sestavení projektu PRJ0034 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0034
dev_langs: C++
helpviewer_keywords: PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b96edfdabeaf4ae31f4eaabb334f56bf29c99c70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0034"></a>Chyba sestavení projektu PRJ0034
Vlastnost 'Další závislosti, pro vlastní úrovni projektu sestavení krok obsažené 'makro, který je vyhodnocen 'macro_expansion'.  
  
 Vlastní krok sestavení na projektu obsahuje chybu v jeho dalších závislost pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamená, že je cesta chybně vytvořen, a to obsahující znaky, nebo kombinace znaků, které jsou neplatné v cestě k souboru.  
  
 Pokud chcete tuto chybu vyřešit, opravte makro nebo odstraňte specifikace cesty. Vyhodnotí cesta je absolutní cestu z adresáře projektu.