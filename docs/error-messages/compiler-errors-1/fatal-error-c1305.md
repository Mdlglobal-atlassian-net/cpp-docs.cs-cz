---
title: Závažná chyba C1305 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b32f9e7555ce905323fd6074d35f1876cd999edd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305
profil databáze 'pgd_file' je pro jinou architekturu  
  
 Soubor .pgd, která byla vygenerována z operace /LTCG:PGINSTRUMENT pro jinou platformu byl předán [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md) jsou k dispozici pro x86 a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy. Však není platný soubor .pgd vygenerovat pomocí operace /LTCG:PGINSTRUMENT pro jednu platformu jako vstup pro /LTCG:PGOPTIMIZE pro různé platformy.  
  
 Pokud chcete tuto chybu vyřešit, předejte pouze .pgd soubor, který je vytvořen s /LTCG:PGINSTRUMENT k /LTCG:PGOPTIMIZE na stejnou platformu.