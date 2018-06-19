---
title: 'OLE – pozadí: Propojování a vkládání | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c5dc7a5770c98323187dbabcd8c2a7bb9eb652de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347276"
---
# <a name="ole-background-linking-and-embedding"></a>OLE – pozadí: Propojování a vkládání
Pomocí příkazu vložení v aplikaci kontejneru vytvořením Vložená součást nebo vložené položky. Zdroj dat pro vložené položky jsou uloženy jako součást OLE dokumentu, který jej obsahuje. Tímto způsobem souboru dokumentu pro dokument aplikace word procesoru může obsahovat text a také může obsahovat rastrové obrázky, grafy, vzorce nebo jiný typ data.  
  
 OLE poskytuje jiný způsob, jak začlenit data z jiné aplikace: vytváření propojená komponenta nebo propojené položky nebo odkaz. Kroky pro vytvoření propojené položky jsou podobná těm pro vytvoření vložené položky, s tím rozdílem, že místo příkazu Vložit použijete příkaz Vložit propojení. Na rozdíl od komponentu embedded propojená komponenta ukládá cestu k původní data, což se často stává v samostatném souboru.  
  
 Například pokud procesor dokument aplikace word pracují a vytvoření propojené položky na některé buňky tabulky, data pro propojené položky uložené v původním dokumentu tabulky. Dokument aplikace word procesoru obsahuje jenom informace o určení, kde položka nachází, to znamená, obsahuje odkaz na původního dokumentu tabulky. Když dvakrát kliknete na buněk tabulky aplikace spuštěna a původního dokumentu tabulky je načtena z kde byl uložen.  
  
 Každá položka OLE zda vložené nebo propojené, má typ přidruženo založené na aplikaci, která ji vytvořila. Například Microsoft Paintbrush položka je jeden typ položky a položku aplikace Microsoft Excel je jiného typu. Některé aplikace, ale můžete vytvořit více než jeden typ položky. Aplikace Microsoft Excel můžete například vytvořit list položky, položky grafu a makra aplikace položky. Každá z těchto položek můžete systém, identifikátor třídy jednoznačně identifikuje nebo **CLSID**.  
  
## <a name="see-also"></a>Viz také  
 [OLE – pozadí](../mfc/ole-background.md)   
 [OLE – pozadí: Kontejnery a servery](../mfc/ole-background-containers-and-servers.md)   
 [Kontejnery: Klientské položky](../mfc/containers-client-items.md)   
 [Servery: Serverové položky](../mfc/servers-server-items.md)

