---
title: Podpora MAPI v MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, MAPI support
- MAPI support in MFC
- CDocument class [MFC], and MAPI
- OnUpdateFileSendMail method [MFC]
- MAPI, MFC
- OnFileSendMail method [MFC]
ms.assetid: cafbecb1-0427-4077-b4b8-159bae5b49b8
ms.openlocfilehash: 3024f744407cf33c8dfad8a6f7af736e0f8061ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356990"
---
# <a name="mapi-support-in-mfc"></a>Podpora MAPI v MFC

Knihovna MFC poskytuje podporu pro podmnožinu rozhraní MAPI (Microsoft Messaging Application Application Application Interface) ve třídě `CDocument`. Konkrétně `CDocument` má členské funkce, které určují, zda je v počítači koncového uživatele přítomna podpora pošty, a pokud ano, povolte příkaz Odeslat poštu, jehož standardní ID příkazu je ID_FILE_SEND_MAIL. Funkce obslužné rutiny knihovny MFC pro tento příkaz umožňuje uživateli odeslat dokument elektronickou poštou.

> [!TIP]
> Přestože knihovna MFC nezapouzdřuje celou sadu funkcí MAPI, můžete stále volat funkce MAPI přímo, stejně jako můžete volat funkce rozhraní API Win32 přímo z programů knihovny MFC.

Poskytnutí příkazu Odeslat poštu v aplikaci je velmi snadné. Knihovna MFC poskytuje implementaci k zabalení `CDocument`dokumentu (to znamená odvozený objekt) jako přílohu a odeslat jako e-mail. Tato příloha je ekvivalentní příkazu Uložit soubor, který ukládá (serializuje) obsah dokumentu do e-mailové zprávy. Tato implementace volá poštovního klienta v počítači uživatele, aby uživateli poskytl možnost adresovat poštu a přidat text předmětu a zprávy do e-mailové zprávy. Uživatelům se zobrazí uživatelské rozhraní jejich známé poštovní aplikace. Tato funkce je poskytována dvěma `CDocument` členskými funkcemi: `OnFileSendMail` a `OnUpdateFileSendMail`.

Mapi potřebuje přečíst soubor k odeslání přílohy. Pokud aplikace udržuje svůj datový `OnFileSendMail` soubor otevřený během volání funkce, je třeba soubor otevřít s režimem sdílení, který umožňuje přístup k souboru více procesům.

> [!NOTE]
> Přepsání `OnFileSendMail` verze for `COleDocument` class správně zpracovává složené dokumenty.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Implementace příkazu Odeslat poštu pomocí knihovny MFC

1. Pomocí editoru nabídek Visual C++ přidejte položku nabídky, jejíž ID příkazů je ID_FILE_SEND_MAIL.

   Toto ID příkazu je poskytována rámci v AFXRES. H. Příkaz lze přidat do libovolné nabídky, ale obvykle se přidá do nabídky **Soubor.**

1. Ručně přidejte do mapy zpráv dokumentu následující:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Tato mapa zpráv funguje pro dokument `CDocument` `COleDocument` odvozený z buď nebo – vobou případech zachytí správnou základní třídu, i když je mapa zpráv ve třídě odvozeného dokumentu.

1. Sestavte si aplikaci.

Pokud je k dispozici podpora pošty, `OnUpdateFileSendMail` knihovna MFC `OnFileSendMail`povolí položku nabídky s příkazem a následně ho zpracuje pomocí příkazu . Pokud podpora pošty není k dispozici, knihovna MFC automaticky odebere položku nabídky, aby ji uživatel neuviděl.

> [!TIP]
> Místo ručního přidávání položek mapy zpráv, jak bylo popsáno výše, můžete pomocí [Průvodce třídou](reference/mfc-class-wizard.md) mapovat zprávy na funkce. Další informace naleznete v [tématu Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Související informace naleznete v přehledu [MAPI.](../mfc/mapi.md)

Další informace o `CDocument` členských funkcích, které umožňují rozhraní MAPI, naleznete v následujících tématech:

- [Cdocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [Cdocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Viz také

[MAPI](../mfc/mapi.md)
