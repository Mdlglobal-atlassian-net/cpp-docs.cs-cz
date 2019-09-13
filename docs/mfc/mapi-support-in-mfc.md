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
ms.openlocfilehash: e46eaf2bd84d4cebd2215ab2752ce3bb8e1eb9b3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907682"
---
# <a name="mapi-support-in-mfc"></a>Podpora MAPI v MFC

MFC poskytuje podporu pro podmnožinu rozhraní MAPI (Messaging Application Program) společnosti Microsoft ve třídě `CDocument`. `CDocument` Konkrétně má členské funkce, které určují, zda je na počítači koncového uživatele k dispozici podpora pošty a v případě potřeby povolte příkaz Odeslat poštu, jehož ID standardního příkazu je ID_FILE_SEND_MAIL. Funkce obslužné rutiny MFC pro tento příkaz umožňuje uživateli odeslat dokument prostřednictvím elektronické pošty.

> [!TIP]
>  I když knihovna MFC nepouzdřuje celou sadu funkcí rozhraní MAPI, můžete i nadále volat funkce rozhraní MAPI přímo, stejně jako můžete volat funkce Win32 API přímo z programů MFC.

Poskytování příkazu pro odeslání pošty ve vaší aplikaci je velmi snadné. Knihovna MFC poskytuje implementaci pro zabalení dokumentu (tj `CDocument`. objektu odvozeného) jako přílohy a jeho odeslání jako e-mailu. Tato příloha je ekvivalentní příkazu k uložení souboru, který ukládá (serializace) obsah dokumentu do e-mailové zprávy. Tato implementace volá klienta pošty na počítači uživatele, aby mohl dát uživateli možnost adresovat e-mail a přidat předmět a text zprávy do e-mailové zprávy. Uživatelé uvidí své známé uživatelské rozhraní e-mailové aplikace. Tato funkce je poskytována dvěma `CDocument` členskými funkcemi: `OnFileSendMail` a `OnUpdateFileSendMail`.

Rozhraní MAPI musí přečíst soubor pro odeslání přílohy. Pokud aplikace udržuje svůj datový soubor otevřený během `OnFileSendMail` volání funkce, soubor musí být otevřen s režimem sdílení, který umožňuje více procesům přístup k souboru.

> [!NOTE]
>  Přepsání verze `OnFileSendMail` pro třídu `COleDocument` správně zpracovává složené dokumenty.

#### <a name="to-implement-a-send-mail-command-with-mfc"></a>Implementace příkazu pro odeslání pošty pomocí MFC

1. Pomocí editoru vizuálních C++ nabídek přidejte položku nabídky, jejíž ID příkazu je ID_FILE_SEND_MAIL.

   Toto ID příkazu je poskytováno rozhraním v AFXRES. Y. Příkaz lze přidat do jakékoli nabídky, je však obvykle přidán do nabídky **soubor** .

1. Do mapy zpráv v dokumentu ručně přidejte následující:

   [!code-cpp[NVC_MFCDocView#9](../mfc/codesnippet/cpp/mapi-support-in-mfc_1.cpp)]

    > [!NOTE]
    >  Toto rozvržení zprávy funguje pro dokument odvozený od `CDocument` nebo `COleDocument` – v obou případech používá správnou základní třídu, a to i v případě, že je mapa zpráv v odvozené třídě dokumentu.

1. Sestavte aplikaci.

Pokud je k dispozici podpora pošty, knihovna MFC povolí položku `OnUpdateFileSendMail` nabídky s a následně zpracuje příkaz `OnFileSendMail`s. Pokud není k dispozici podpora pošty, knihovna MFC automaticky odebere položku nabídky, aby ji uživatel neuvidí.

> [!TIP]
>  Místo ručního přidávání položek mapování zpráv, jak je popsáno výše, můžete použít [Průvodce třídou](reference/mfc-class-wizard.md) třídy k mapování zpráv na funkce. Další informace najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Související informace najdete v tématu Přehled [rozhraní MAPI](../mfc/mapi.md) .

Další informace o `CDocument` členských funkcích, které povolují rozhraní MAPI, najdete v těchto tématech:

- [Objektu CDocument:: OnFileSendMail](../mfc/reference/cdocument-class.md#onfilesendmail)

- [CDocument::OnUpdateFileSendMail](../mfc/reference/cdocument-class.md#onupdatefilesendmail)

- [COleDocument::OnFileSendMail](../mfc/reference/coledocument-class.md#onfilesendmail)

## <a name="see-also"></a>Viz také:

[MAPI](../mfc/mapi.md)
