---
title: MAPI | Microsoft Docs
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
ms.openlocfilehash: 1df0d00aa6356fa1741e7f4fc34d8063782da859
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930671"
---
# <a name="mapi"></a>MAPI
Tento článek popisuje Microsoft Zasílání zpráv rozhraní MAPI (Application Programming) pro vývojáře aplikací zpráv klienta. MFC poskytuje podporu pro podmnožinu rozhraní MAPI v třídě `CDocument` , ale není zapouzdření celý rozhraní API. Další informace najdete v tématu [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md).  
  
 MAPI je sada funkcí, které poštovní a e-mailu podporou aplikace použít k vytvoření, manipulaci, přenos a ukládání e-mailových zpráv. To poskytuje vývojářům aplikací definovat účel a obsah e-mailových zpráv nástroje a poskytuje flexibilitu v jejich správu uložené e-mailových zpráv. MAPI taky poskytuje jednotné rozhraní, které vývojáři aplikace můžete použít k vytvoření, poštovní a e-mailu aplikací nezávislé systému pro zasílání zpráv.  
  
 Klienti zasílání zpráv poskytují lidského rozhraní pro interakci s Microsoft Windows zasílání zpráv systému (WMS). Tato interakce obvykle zahrnuje požaduje služby od takovou poskytovatelů, jako je například úložiště zpráv a adresářů.  
  
 Další informace o rozhraní MAPI najdete v článcích v části průvodce v Win32 MAPI (Messaging) sady Windows SDK.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)   
 [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)   
 [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

