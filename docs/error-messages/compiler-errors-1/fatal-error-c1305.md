---
title: Závažná chyba C1305 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1305
dev_langs:
- C++
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3cb1cf19d0fc4152fbb458d684972bb5a4418f37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227144"
---
# <a name="fatal-error-c1305"></a>Závažná chyba C1305
profil databáze 'pgd_file' je pro jinou architekturu  
  
 Soubor .pgd, která byla vygenerována z operace /LTCG:PGINSTRUMENT pro jinou platformu byl předán [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Optimalizace na základě profilu](../../build/reference/profile-guided-optimizations.md) jsou k dispozici pro x86 a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] platformy. Však není platný soubor .pgd vygenerovat pomocí operace /LTCG:PGINSTRUMENT pro jednu platformu jako vstup pro /LTCG:PGOPTIMIZE pro různé platformy.  
  
 Pokud chcete tuto chybu vyřešit, předejte pouze .pgd soubor, který je vytvořen s /LTCG:PGINSTRUMENT k /LTCG:PGOPTIMIZE na stejnou platformu.