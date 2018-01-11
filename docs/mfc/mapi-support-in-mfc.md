---
title: Podpora MAPI v MFC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a6cc1670559354628127729724300399d5f003ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mapi-support-in-mfc"></a>Podpora MAPI v MFC
MFC poskytuje podporu pro podmnožinu z Microsoft Zasílání zpráv programu rozhraní MAPI (Application) ve třídě **CDocument**. Konkrétně **CDocument** má členské funkce, které určují, zda je na počítači koncového uživatele pro podporu pošty a pokud ano, povolit příkaz Odeslat e-mailu s ID standardních příkazů **ID_FILE_SEND_MAIL**. Funkce MFC obslužná rutina pro tento příkaz umožňuje uživatelům poslat dokument e-mailem.  
  
> [!TIP]
>  I když MFC není zapouzdření celou sadu funkce MAPI, můžete stále volat MAPI funkce přímo, stejně jako funkce rozhraní API Win32 můžete volat přímo z MFC programy.  
  
 Poskytnutí odesílání pošty příkaz v aplikaci je velmi snadné. MFC poskytuje implementaci pro balíček dokumentu (to znamená, **CDocument**-odvozené objektu) jako přílohu a odeslání v e-mailu. Toto připojení je ekvivalentní příkaz Uložit soubor, který uloží (serializuje) obsah dokumentu a e-mailovou zprávu. Tato implementace volá na e-mailového klienta na počítači uživatele a přidělit uživateli možnost e-mailu a přidání předmět a text zprávy do e-mailovou zprávu. Uživatelé zobrazit uživatelské rozhraní aplikace jejich známých e-mailu. Tato funkce poskytuje dva **CDocument** členské funkce: `OnFileSendMail` a `OnUpdateFileSendMail`.  
  
 MAPI musí přečíst soubor k odeslání přílohy. Pokud aplikace udržuje jeho datový soubor otevřete během `OnFileSendMail` volání funkce, soubor je nutné otevřít s režimem sdílenou složku, která umožňuje více procesů pro přístup k souboru.  
  
> [!NOTE]
>  Přepsání verzi `OnFileSendMail` pro třídu `COleDocument` správně obslužné rutiny složené dokumenty.  
  
#### <a name="to-implement-a-send-mail-command-with-mfc"></a>K implementaci příkaz Odeslat e-mailu s MFC  
  
1.  Použití editoru nabídky Visual C++ pro přidání položky nabídky, jehož ID příkazu je **ID_FILE_SEND_MAIL**.  
  
     Toto ID příkazu je poskytovaný rozhraní v AFXRES. H. Příkaz přidáním jakékoli nabídky, ale je obvykle přidán do **souboru** nabídky.  
  
2.  Mapy zpráv vašeho dokumentu ručně přidejte následující:  
  
     [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]  
  
    > [!NOTE]
    >  Tato mapa zpráv funguje pro dokument odvozené od buď **CDocument** nebo **COleDocument** – ho převezme správné základní třídu v obou případech, i když mapy zpráv v odvození dokumentové třídy.  
  
3.  Sestavení aplikace.  
  
 Pokud je k dispozici podpora e-mailu, MFC umožňuje vaší položky nabídky s `OnUpdateFileSendMail` a následně zpracuje příkaz s `OnFileSendMail`. Pokud není k dispozici podpora e-mailu, MFC automaticky odebere vaší položky nabídky, aby uživatel neuvidí.  
  
> [!TIP]
>  Místo ručně přidávání položek mapování zpráv výše popsané, můžete v okně Vlastnosti třídy mapovat zpráv na funkce. Další informace najdete v tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md).  
  
 Související informace najdete v tématu [MAPI](../mfc/mapi.md) Přehled.  
  
 Další informace o **CDocument** členské funkce, které umožňují MAPI, najdete v části:  
  
-   [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)  
  
-   [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)  
  
-   [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)  
  
## <a name="see-also"></a>Viz také  
 [MAPI](../mfc/mapi.md)

