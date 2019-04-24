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
ms.openlocfilehash: 9b873ca1b3384adab6487fb3af9dc1401aaad12c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225523"
---
# <a name="mapi-support-in-mfc"></a>Podpora MAPI v MFC

Knihovna MFC poskytuje podporu pro podmnožinu z Microsoft Application Program rozhraní MAPI (Messaging) ve třídě `CDocument`. Konkrétně `CDocument` má členské funkce, které určují, zda je na počítači koncového uživatele pro podporu e-mailu a pokud ano, povolit odeslat poštu příkaz, jehož ID standardní příkaz je ID_FILE_SEND_MAIL. Funkce obslužné rutiny knihovny MFC pro tento příkaz umožňuje uživateli poslat dokument e-mailem.

> [!TIP]
>  I když MFC nejsou zapouzdření celou sadu funkce MAPI, můžete stále volat rozhraní MAPI funkce přímo, stejně jako funkce rozhraní Win32 API můžete volat přímo z aplikace knihovny MFC.

Příkaz v aplikaci je jednoduché a poskytování odeslat e-mailu. Knihovna MFC poskytuje implementaci pro balíček dokumentu (to znamená `CDocument`-odvozenému objektu) jako přílohu a odeslat ho jako e-mailu. Je ekvivalentní k příkazu Uložit soubor, který uloží tuto přílohu (serializuje) obsah dokumentu a e-mailovou zprávu. Tato implementace vyzývá poštovního klienta na počítač uživatele a přidělit uživateli příležitost k řešení e-mailu a přidání předmět a text zprávy do e-mailovou zprávu. Uživatelé uvidí jejich známých poštovní aplikaci uživatelského rozhraní. Tato funkce je poskytnut pomocí dvou `CDocument` členské funkce: `OnFileSendMail` a `OnUpdateFileSendMail`.

Rozhraní MAPI potřebuje číst soubor k odeslání přílohy. Pokud aplikace si zachová svůj datový soubor otevřít během `OnFileSendMail` volání funkce, soubor je potřeba otevřít s režimem sdílenou složku, která umožňuje přístup k souboru mezi více procesy.

> [!NOTE]
>  Přepsání verze `OnFileSendMail` pro třídu `COleDocument` správně zpracovává složené dokumenty.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Implementace příkazu Odeslat e-mailu s knihovnou MFC

1. Tento vizuál použít C++ editor nabídek k přidání položky nabídky, jejichž ID příkazu je ID_FILE_SEND_MAIL.

   Toto ID příkazu je poskytovaného rámcem v AFXRES. H. Příkaz je přidat do jakékoli nabídky, ale obvykle je přidána do **souboru** nabídky.

1. Ručně přidejte následující text do mapy dokumentu zpráva:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Toto mapování zpráv se dá použít pro dokumentu odvozen od buď `CDocument` nebo `COleDocument` – použila správné základní třídy v obou případech, přestože je ve své třídě odvozené dokumentu mapování zprávy.

1. Sestavení aplikace.

Pokud je k dispozici podpora e-mailu, MFC umožňuje položku nabídky s `OnUpdateFileSendMail` a následně zpracuje příkaz s `OnFileSendMail`. Pokud není k dispozici podpora e-mailu, MFC automaticky odstraní položku nabídky tak, že uživatel neuvidí.

> [!TIP]
>  Místo ruční přidávání položek mapování zprávu, jak je uvedeno výše, můžete v okně Vlastnosti třídy mapování zpráv na funkce. Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Související informace naleznete v tématu [MAPI](../mfc/mapi.md) Přehled.

Další informace o `CDocument` členské funkce, které umožňují MAPI, naleznete v tématu:

- [CDocument::OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Viz také:

[MAPI](../mfc/mapi.md)
