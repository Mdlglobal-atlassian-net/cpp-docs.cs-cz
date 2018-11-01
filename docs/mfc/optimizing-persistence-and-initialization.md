---
title: Optimalizace trvalosti a inicializace
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 6f0d888f49cf27505882e89e3cdbb469ea9e8684
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472693"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimalizace trvalosti a inicializace

Ve výchozím nastavení, trvalosti a inicializace v ovládacím prvku jsou zpracovávány `DoPropExchange` členskou funkci. V typické ovládacího prvku, tato funkce obsahuje volání do několika **PX_** funkcí (`PX_Color`, `PX_Font`, a tak dále), jeden pro každou vlastnost.

Tento přístup má výhodu v tom, který jeden `DoPropExchange` implementace je možné pro inicializaci, přetrvávání v binárním formátu a přetrvání takzvané "vlastnosti kontejneru" formát používaný čtečkou několik kontejnerů. Tato jedna funkce obsahuje všechny informace o vlastnosti a jejich výchozí hodnoty na jednom místě.

Tato obecnosti však dodává za cenu efektivitu. **PX_** funkce získat jejich flexibilitu prostřednictvím s více vrstvami implementace, které jsou ze své podstaty méně efektivní než více s přímým přístupem, ale méně flexibilní, přístupy. Kromě toho pokud ovládací prvek předává výchozí hodnotu **PX_** fungovala, že pokaždé, když, dokonce i v situacích, například při nemusí být použita výchozí hodnota musí být zadaná výchozí hodnota. Pokud generování výchozí hodnota je jednoduché úlohy (například pokud je hodnota získána z změní vlastnost ambient) a potom nadbytečné, zbytečné práce provádí v případech, kdy se nepoužívá výchozí hodnotu.

Může zlepšit výkon binární trvalost ovládacího prvku tak, že přepíšete ovládacího prvku `Serialize` funkce. Výchozí implementace tato členská funkce zavolá na váš `DoPropExchange` funkce. Tak, že jej přepíšete, můžete zadat více přímou implementaci binární trvalosti. Představte si třeba to `DoPropExchange` funkce:

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

Pro zlepšení výkonu binární trvalého tohoto ovládacího prvku, je možné přepsat `Serialize` funkce takto:

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion` Lokální proměnné lze použít ke zjištění verze trvalý stav ovládacího prvku se načtení nebo uložení. Pomocí této proměnné můžete namísto volání metody [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion).

Pro úsporu místa trochu v trvalém formátu pro **BOOL** vlastnost (a aby byl kompatibilní s formátem vytvářených `PX_Bool`), můžete uložit vlastnost jako **BAJTŮ**, následujícím způsobem:

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

Všimněte si, že v případě zatížení se používá dočasnou proměnnou a pak přiřadí její hodnotu, nikoli přetypování *m_boolProp* k **BAJTŮ** odkaz. Metoda přetypování způsobí pouze jeden bajt *m_boolProp* upravovaného, byste museli opustit zbývající bajty neinicializovaná.

Pro stejný ovládací prvek, lze optimalizovat inicializace ovládacího prvku tak, že přepíšete [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) následujícím způsobem:

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

I když `Serialize` a `OnResetState` přepsány, `DoPropExchange` funkce by měly být neustále beze změny vzhledem k tomu, že je stále používané pro trvalost ve formátu kontejneru objektů a dat. Je důležité zachovat všechny tři z těchto funkcí k zajištění, že ovládací prvek spravuje její vlastnosti, bez ohledu na to, které trvalost používá mechanismus kontejneru.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

