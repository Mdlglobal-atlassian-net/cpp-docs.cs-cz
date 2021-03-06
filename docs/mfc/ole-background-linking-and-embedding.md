---
title: 'OLE – pozadí: Propojování a vkládání'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE embedded items [MFC]
- item types [MFC], defined
- item types [MFC]
- OLE [MFC], linked items
- linked items (OLE) [MFC]
- embedded objects [MFC]
- OLE items [MFC], types
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
ms.openlocfilehash: 02607df2a8fa086c5751f2b446e349a3efdbcd20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186799"
---
# <a name="ole-background-linking-and-embedding"></a>OLE – pozadí: Propojování a vkládání

Pomocí příkazu Vložit do aplikace typu kontejner můžete vytvořit aplikace Vložená součást nebo vloženou položku. Zdrojová data vložená položka je uložená jako část dokumentu OLE, který jej obsahuje. Tímto způsobem soubor dokumentu pro textový procesor dokumentu může obsahovat text a také může obsahovat rastrové obrázky, grafy, vzorce nebo jakéhokoli jiného typu data.

Dalším způsobem, jak využívat data z jiné aplikace poskytuje OLE: vytváření propojená komponenta nebo propojená položka nebo odkaz. Kroky pro vytvoření propojené položky jsou podobná těm pro vytvoření vloženou položku s tím rozdílem, že pomocí příkazu propojit místo příkaz Paste. Na rozdíl od komponentu vložený úložišť propojená komponenta cestu k původní data, což se často stává v samostatném souboru.

Například pokud pracujete v textovém dokumentu procesoru a vytvoření propojené položky do některých buněk tabulky, propojené položky jsou data uložená v původním dokumentu tabulky. Textový procesor dokument obsahuje jenom informace o určení, kde položka najdete, to znamená, že obsahuje odkaz na původní dokument tabulka. Když dvakrát kliknete buňky tabulky aplikace se spustí a původní dokument tabulka je načtena z kde byl uložen.

Každá položka OLE, zda vložený nebo připojený, má typ přidruženo podle aplikace, která ho vytvořila. Například Microsoft Paintbrush položka je jeden typ položky a položku Microsoft Excel je jiného typu. Některé aplikace, ale můžete vytvořit více než jeden typ položky. Aplikace Microsoft Excel můžete například vytvořit list položek, graf položek a položek makra aplikace. Každá z těchto položek mohou být jednoznačně identifikují pomocí systému pomocí identifikátoru třídy nebo **CLSID**.

## <a name="see-also"></a>Viz také:

[OLE – pozadí](../mfc/ole-background.md)<br/>
[OLE – pozadí: Kontejnery a servery](../mfc/ole-background-containers-and-servers.md)<br/>
[Kontejnery: Klientské položky](../mfc/containers-client-items.md)<br/>
[Servery: Serverové položky](../mfc/servers-server-items.md)
