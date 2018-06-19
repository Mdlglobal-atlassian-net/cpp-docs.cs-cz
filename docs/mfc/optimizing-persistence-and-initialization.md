---
title: Optimalizace trvalosti a inicializace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e528ea7901518112c255eefbfb1e674fddee04e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355657"
---
# <a name="optimizing-persistence-and-initialization"></a>Optimalizace trvalosti a inicializace
Ve výchozím nastavení, trvalosti a inicializace v ovládacím prvku jsou zpracovávány `DoPropExchange` – členská funkce. V ovládacím prvku typické tuto funkci obsahuje volání do několika **PX_** funkce (`PX_Color`, `PX_Font`a tak dále), jeden pro každou vlastnost.  
  
 Tento přístup má výhodu, který jednoho `DoPropExchange` implementace lze použít pro inicializaci trvalosti v binárním formátu a trvalosti v takzvané "vlastnost kontejneru" formát používaný některé kontejnery. Tato funkce jeden poskytuje všechny informace o vlastnostech a jejich výchozí hodnoty v jednom vhodném umístění.  
  
 Tato obecné však obsahuje za cenu efektivitu. **PX_** funkce získat jejich flexibilitě prostřednictvím s více vrstvami implementace, které jsou ze své podstaty méně efektivní než více direct, ale méně flexibilní přístupy. Kromě toho v případě úspěšného výchozí hodnotu do ovládacího prvku **PX_** fungovat, že pokaždé, když, i v situacích, například při nemusí být použita výchozí hodnota je třeba zadat výchozí hodnotu. Pokud generování výchozí hodnota je triviální úloh (například pokud je hodnota získána z vedlejším vlastnosti) a potom navíc, nepotřebné pracovní se provádí v případech, kdy není použita výchozí hodnota.  
  
 Můžete zlepšit výkon binární trvalost ovládacího prvku přepsáním ovládacího prvku `Serialize` funkce. Výchozí implementace této funkce člen zavolá na váš `DoPropExchange` funkce. Jeho přepsání, můžete poskytnout více přímé implementace binární trvalosti. Zvažte například to `DoPropExchange` funkce:  
  
 [!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]  
  
 Pokud chcete zlepšit výkon binární trvalost tento ovládací prvek, je možné přepsat `Serialize` funkce následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]  
  
 `dwVersion` Místní proměnné lze použít ke zjištění verze trvalý stav ovládacího prvku se načíst nebo uložit. Pomocí této proměnné můžete místo volání [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion).  
  
 Ušetřit místo na trochu v trvalém formátu pro **BOOL** vlastnost (, která bude kompatibilní s formátem vyprodukované `PX_Bool`), můžete uložit jako vlastnost **BAJTŮ**, a to takto:  
  
 [!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]  
  
 Upozorňujeme, že v případě zatížení dočasné proměnná se používá, a pak je jeho hodnota přiřazen, nikoli přetypování `m_boolProp` k **BAJTŮ** odkaz. Přetypování technika by způsobilo pouze jeden bajt `m_boolProp` upravována, ponechat zbývající bajty Neinicializovaný.  
  
 Pro stejný ovládací prvek, můžete optimalizovat ovládacího prvku inicializace přepsání [COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate) následujícím způsobem:  
  
 [!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]  
  
 I když `Serialize` a `OnResetState` byl potlačen, `DoPropExchange` funkce by měly být udržovány beze změn protože je stále používán trvalosti ve formátu kontejneru objektů. Je důležité zachovat všechny tři z těchto funkcí k zajištění, že ovládací prvek spravuje jeho vlastnosti konzistentně, bez ohledu na to, které trvalost používá mechanismus kontejneru.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX: Optimalizace](../mfc/mfc-activex-controls-optimization.md)

