---
title: MAPI | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messaging [MFC], client applications
- enabling applications for MAPI [MFC]
- MAPI support in MFC
- e-mail [MFC], enabling
- mail [MFC], enabling your application
- MAPI, MFC
- enabling applications for mail [MFC]
ms.assetid: 193449f7-b131-4ab0-9301-8d4f6cd1e7c4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 505b9b16bb3c84e92a640f136c5aa58fdaaa13a5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mapi"></a>MAPI
Tento článek popisuje Microsoft Zasílání zpráv rozhraní MAPI (Application Programming) pro vývojáře aplikací zpráv klienta. MFC poskytuje podporu pro podmnožinu rozhraní MAPI v třídě **CDocument** , ale není zapouzdření celý rozhraní API. Další informace najdete v tématu [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md).  
  
 MAPI je sada funkcí, které poštovní a e-mailu podporou aplikace použít k vytvoření, manipulaci, přenos a ukládání e-mailových zpráv. To poskytuje vývojářům aplikací definovat účel a obsah e-mailových zpráv nástroje a poskytuje flexibilitu v jejich správu uložené e-mailových zpráv. MAPI taky poskytuje jednotné rozhraní, které vývojáři aplikace můžete použít k vytvoření, poštovní a e-mailu aplikací nezávislé systému pro zasílání zpráv.  
  
 Klienti zasílání zpráv poskytují lidského rozhraní pro interakci s Microsoft Windows zasílání zpráv systému (WMS). Tato interakce obvykle zahrnuje požaduje služby od takovou poskytovatelů, jako je například úložiště zpráv a adresářů.  
  
 Další informace o rozhraní MAPI najdete v článcích v části průvodce v Win32 MAPI (Messaging) sady Windows SDK.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Podpora MAPI v MFC](../mfc/mapi-support-in-mfc.md)  
  
## <a name="see-also"></a>Viz také  
 [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)   
 [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)   
 [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

