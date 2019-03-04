---
title: MAPI
ms.date: 11/04/2016
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
ms.openlocfilehash: a5f60e1ba8c2b68ddca312859694f532e38da965
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279104"
---
# <a name="mapi"></a>MAPI

Tento článek popisuje společnosti Microsoft Zasílání zpráv rozhraní MAPI (Application Programming) pro vývojáře aplikací zprávy klienta. Knihovna MFC poskytuje podporu pro celou dílčí sadu rozhraní MAPI ve třídě `CDocument` , ale ne zapouzdření celé rozhraní API. Další informace najdete v tématu [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md).

Rozhraní MAPI je sada funkcí, které používají aplikace s povoleným e-mailem a s ohledem na e-mailu k vytváření, manipulaci s, přenosu a uložení e-mailové zprávy. Aplikace vývojářům poskytuje nástroje k definování účel a obsah e-mailové zprávy a poskytuje flexibilitu v jejich správu uloženého e-mailové zprávy. Rozhraní MAPI také poskytuje společné rozhraní, která vývojářům aplikací můžete použít k vytvoření, poštovní a aplikací pracujících s e-mailu nezávisle na základní systému zasílání zpráv.

Klienti zasílání zpráv poskytuje lidské rozhraní pro interakci s Microsoft Windows zasílání zpráv systému (WMS). Tato interakce obvykle zahrnuje žádosti o služby od takovou poskytovatelů, jako je například úložiště zpráv a adresáře.

Další informace o rozhraní MAPI najdete v článcích v části průvodce v systému Win32 rozhraní MAPI (Messaging) sady Windows SDK.

## <a name="in-this-section"></a>V tomto oddílu

[Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md)

## <a name="see-also"></a>Viz také:

[CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)<br/>
[CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)<br/>
[COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)
