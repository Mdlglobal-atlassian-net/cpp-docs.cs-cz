---
title: ROZHRANÍ MAPI | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2ca182da3a0300604415b790c0aba138c8fd7a2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46439104"
---
# <a name="mapi"></a>MAPI

Tento článek popisuje společnosti Microsoft Zasílání zpráv rozhraní MAPI (Application Programming) pro vývojáře aplikací zprávy klienta. Knihovna MFC poskytuje podporu pro celou dílčí sadu rozhraní MAPI ve třídě `CDocument` , ale ne zapouzdření celé rozhraní API. Další informace najdete v tématu [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md).

Rozhraní MAPI je sada funkcí, které používají aplikace s povoleným e-mailem a s ohledem na e-mailu k vytváření, manipulaci s, přenosu a uložení e-mailové zprávy. Aplikace vývojářům poskytuje nástroje k definování účel a obsah e-mailové zprávy a poskytuje flexibilitu v jejich správu uloženého e-mailové zprávy. Rozhraní MAPI také poskytuje společné rozhraní, která vývojářům aplikací můžete použít k vytvoření, poštovní a aplikací pracujících s e-mailu nezávisle na základní systému zasílání zpráv.

Klienti zasílání zpráv poskytuje lidské rozhraní pro interakci s Microsoft Windows zasílání zpráv systému (WMS). Tato interakce obvykle zahrnuje žádosti o služby od takovou poskytovatelů, jako je například úložiště zpráv a adresáře.

Další informace o rozhraní MAPI najdete v článcích v části průvodce v systému Win32 rozhraní MAPI (Messaging) sady Windows SDK.

## <a name="in-this-section"></a>V tomto oddílu

[Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Viz také

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

