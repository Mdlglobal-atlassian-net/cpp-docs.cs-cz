---
title: "Zabezpečení Internetu (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a44e528e871d784c432730799c44ac91af465be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="internet-security-c"></a>Internetové zabezpečení (C++)
Zabezpečení kódu je závažný problém pro vývojáře a pro uživatele internetových aplikací. Jsou rizika: škodlivý kód, kód, který byl porušen a kód z neznámé lokality nebo autoři.  
  
 Existují dva základní přístupy k zabezpečení při vývoji pro Internet. První se označuje jako "sandboxing." V tomto přístupu aplikace omezen na konkrétní sadu rozhraní API a vyloučené z potenciálně nebezpečná ty, které jsou například kde může program zničí data v počítači uživatele vstupně-výstupní soubor. Druhá je implementovaná pomocí digitálních podpisů. Tento postup se označuje jako "shrinkwrap" pro Internet. Kód ověření a podepsaný pomocí privátní klíč a veřejného klíče technologie. Před spuštěním kódu je zajistit, že kódu je ze známé ověřené zdroje a že vzhledem k tomu, že byl podepsán nebyl změněn kód ověřit digitální podpis.  
  
 V prvním případě důvěřujete, že aplikace nebude žádné zlé a důvěřujete počátek aplikace. Digitální podpisy za sekundu, se používají k ověření pravosti. Digitální podepisování je oborový standard používá k identifikaci a poskytují podrobné informace o vydavateli kódu. Jeho technologie je založena na standardech, včetně RSA a X.509. Prohlížeče obvykle umožňují uživatelům si vybrat, zda chtějí stáhnout a spustit kódem neznámého původu.  
  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

