---
title: Internetové zabezpečení (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: e7892793a82f2b030a99465a712e33e1b9ef4673
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486096"
---
# <a name="internet-security-c"></a>Internetové zabezpečení (C++)

Bezpečnostní kód je závažný problém pro vývojáře a uživatele internetových aplikací. Existují rizika: škodlivý kód, kód, který bylo manipulováno a kód z neznámého nebo autoři.

Existují dva základní přístupy k zabezpečení při vývoji pro Internet. První se nazývá "izolace (sandbox)." V takovém případě aplikaci omezit na konkrétní sadu rozhraní API a vyloučit z potenciálně nebezpečné ty, jako jsou například vstupně, kde může program zničí data v počítači uživatele. Druhá je implementováno pomocí digitálních podpisů. Tento postup se označuje jako "shrinkwrap" pro Internet. Kód je ověřený a podepsán pomocí klíčových technologií privátní klíč/public. Předtím, než je kód spuštěn, je ověřit digitální podpis, ujistěte se, že kód je ze známého ověřeného zdroje a kód nebyl byla změněna, protože byla podepsána.

V prvním případě důvěřovat, že aplikace nebude provádět žádné a původu aplikace důvěřujete. V druhém digitální podpisy se používají k ověření pravosti. Digitální podpis je oborový standard lze identifikovat a zadat další informace o vydavateli kód. Technologie je založena na standardech, včetně RSA a X.509. Prohlížeče obvykle umožňují uživatelům si vybrat, zda chtějí stáhnout a spustit kód neznámého původu.

## <a name="see-also"></a>Viz také

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

