---
title: Zabezpečení Internetu (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- code signing [MFC], Internet security
- sandboxing [MFC]
- digital signatures [MFC], Internet security
- code signing [MFC]
- Web application security [MFC]
- code access security [MFC], Internet security considerations
- security [MFC]
- security [MFC], Internet
- Internet applications [MFC], security
- Web application security [MFC], Internet security approaches
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4454eceae2cc5f2e6b46510fe95889c664a568a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="internet-security-c"></a>Internetové zabezpečení (C++)
Zabezpečení kódu je závažný problém pro vývojáře a pro uživatele internetových aplikací. Jsou rizika: škodlivý kód, kód, který byl porušen a kód z neznámé lokality nebo autoři.  
  
 Existují dva základní přístupy k zabezpečení při vývoji pro Internet. První se označuje jako "sandboxing." V tomto přístupu aplikace omezen na konkrétní sadu rozhraní API a vyloučené z potenciálně nebezpečná ty, které jsou například kde může program zničí data v počítači uživatele vstupně-výstupní soubor. Druhá je implementovaná pomocí digitálních podpisů. Tento postup se označuje jako "shrinkwrap" pro Internet. Kód ověření a podepsaný pomocí privátní klíč a veřejného klíče technologie. Před spuštěním kódu je zajistit, že kódu je ze známé ověřené zdroje a že vzhledem k tomu, že byl podepsán nebyl změněn kód ověřit digitální podpis.  
  
 V prvním případě důvěřujete, že aplikace nebude žádné zlé a důvěřujete počátek aplikace. Digitální podpisy za sekundu, se používají k ověření pravosti. Digitální podepisování je oborový standard používá k identifikaci a poskytují podrobné informace o vydavateli kódu. Jeho technologie je založena na standardech, včetně RSA a X.509. Prohlížeče obvykle umožňují uživatelům si vybrat, zda chtějí stáhnout a spustit kódem neznámého původu.  
  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

