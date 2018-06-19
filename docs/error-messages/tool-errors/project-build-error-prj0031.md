---
title: Chyba sestavení projektu PRJ0031 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5ebd25c239a05c4300b574ec0d47035904187d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318318"
---
# <a name="project-build-error-prj0031"></a>Chyba sestavení projektu PRJ0031
Vlastnost 'výstupy, pro vlastní sestavovací krok pro 'file' obsažené 'Makro souboru, který vyhodnocuje se na 'macro_expansion'.  
  
 Vlastní krok sestavení na soubor měl chybný výstup pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamená, že je cesta chybně vytvořen, a to obsahující znaky, nebo kombinace znaků, které jsou neplatné v cestě k souboru.  
  
 Pokud chcete tuto chybu vyřešit, opravte makro nebo odstraňte specifikace cesty. Vyhodnotí cesta je absolutní cestu z adresáře projektu.