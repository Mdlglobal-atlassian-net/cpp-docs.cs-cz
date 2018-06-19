---
title: Obsahování pro aktivní dokument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74ad16aa453c6fa0df2c84bd0a0a789b05f83169
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332670"
---
# <a name="active-document-containment"></a>Práce s kontejnery aktivních dokumentů
Obsahování pro aktivní dokument je technologie, která poskytuje jeden rámec, ve kterém pro práci s dokumenty, namísto nutnosti vytvořit a použít více snímků aplikace pro každý typ dokumentu. V tomto OLE funguje s vložené objekty v rámci složeného dokumentu, ve kterém může být aktivní pouze jediný obsah, liší se od základní technologie OLE. V případě obsahování pro aktivní dokument aktivovat celý dokument (tedy celou aplikaci, včetně přidružených nabídek, panely nástrojů a tak dále) v kontextu jeden snímek.  
  
 Technologie členství ve skupině aktivní dokument byl původně vytvořen pro Microsoft Office pro implementaci vazby sady Office. Však tato technologie je dostatečně flexibilní na podporu kontejnery pro aktivní dokument než vazby sady Office a může podporovat servery dokumentu než aplikace Office a kompatibilní Office.  
  
 Je volána aplikace, který je hostitelem aktivní dokumenty [kontejner pro aktivní dokument](../mfc/active-document-containers.md). Příkladem takových kontejnery jsou vazač Microsoft Office nebo aplikace Microsoft Internet Explorer.  
  
 Obsahování pro aktivní dokument je implementovaná jako sada rozšíření OLE dokumentů, složeného dokumentu technologie OLE. Rozšíření jsou další rozhraní, které umožňují li, místní objekt představující celý dokument místo jediný vložený obsah. Stejně jako u OLE – dokumenty, používá obsahování pro aktivní dokument do kontejneru, který poskytuje místo zobrazení pro aktivní dokumenty a serverů, které poskytují rozhraní a manipulace s možností uživatele pro aktivní dokumenty sami.  
  
 [Server pro aktivní dokument](../mfc/active-document-servers.md) je aplikace (například Word, Excel nebo PowerPoint), která podporuje jeden nebo více třídy aktivních dokumentů, kde každý samotného objektu podporuje rozhraní rozšíření, které umožňují objekt, který má být aktivována v vhodný kontejneru.  
  
 [Aktivní dokument](../mfc/active-documents.md) (poskytuje se z aktivních dokumentů serveru jako je například Word či Excel) je v podstatě plnohodnotném, konvenční dokument, který je vložený objekt v rámci jiný kontejner pro aktivní dokument. Na rozdíl od vložené objekty aktivní dokumenty mít plnou kontrolu nad jejich stránky a k dispozici pro uživatele upravovat je úplné rozhraní aplikace (se všechny jeho základní příkazy a nástroje).  
  
 Aktivní dokument je nejlépe srozumitelné odlišující jej od standardní vložený objekt OLE. Konvence OLE vložený objekt je ten, který se zobrazí v rámci dané stránky dokumentu, který je jeho vlastníkem, a v dokumentu spravuje kontejner OLE. Kontejner ukládá data vložený objekt s zbývající části dokumentu. Vložené objekty se však omezená, že nemají vliv na stránku, na které se objeví.  
  
 Uživatelé aplikace kontejnerů pro aktivní dokument můžete vytvořit aktivní dokumenty (nazývané části vazby sady Office) pomocí Oblíbené aplikací (za předpokladu, že tyto aplikace jsou aktivní dokument povolené), ještě uživatele můžete spravovat výsledný projekt jako jedna entita, která může být jednoznačně s názvem, uložit, vytisknout, a tak dále. Stejným způsobem může uživatel internetovém prohlížeči považovat celá síť, jakož i systémy místního souboru jako entita úložiště jednotlivý dokument možnost Procházet dokumenty v této úložiště z jednoho umístění.  
  
## <a name="sample-programs"></a>Ukázkové aplikace  
  
-   [MFCBIND](../visual-cpp-samples.md) ukázka znázorňuje implementaci aplikace kontejnerů pro aktivní dokument.  
  
## <a name="see-also"></a>Viz také  
 [MFC COM](../mfc/mfc-com.md)

