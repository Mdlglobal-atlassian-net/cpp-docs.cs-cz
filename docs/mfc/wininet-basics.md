---
title: WinInet – základy
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: b989e5c3df63ee7b5129d01468a0f869772ed286
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367327"
---
# <a name="wininet-basics"></a>WinInet – základy

Pomocí wininet můžete přidat podporu FTP ke stažení a nahrávání souborů z vaší aplikace. Můžete přepsat [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) a použít *parametr dwContext* k poskytování informací o průběhu uživatelům při hledání a stahování souborů.

Tento článek obsahuje následující témata:

- [Vytvoření velmi jednoduchého prohlížeče](#_core_create_a_very_simple_browser)

- [Stažení webové stránky](#_core_download_a_web_page)

- [FTP soubor](#_core_ftp_a_file)

- [Načtení gopherský adresář](#_core_retrieve_a_gopher_directory)

- [Zobrazení informací o průběhu při přenosu souborů](#_core_display_progress_information_while_transferring_files)

Níže uvedené výňatky kódu ukazují, jak vytvořit jednoduchý prohlížeč, stáhnout webovou stránku, FTP soubor a vyhledat soubor gopher. Nejsou určeny jako úplné příklady a ne všechny obsahují zpracování výjimek.

Další informace o wininet, naleznete [v tématu Win32 Internet Extensions (WinInet)](../mfc/win32-internet-extensions-wininet.md).

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a>Vytvoření velmi jednoduchého prohlížeče

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a>Stažení webové stránky

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a>FTP soubor

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a>Načtení gopherský adresář

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Použít OnStatusCallback

Při použití tříd WinInet můžete k načtení informací o stavu použít člen [OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) objektu [CInternetSession](../mfc/reference/cinternetsession-class.md) vaší aplikace. Pokud odvodíte `CInternetSession` vlastní `OnStatusCallback`objekt, přepíšete a povolíte `OnStatusCallback` zpětná volání stavu, knihovna MFC zavolá vaši funkci s informacemi o průběhu všech aktivit v této relaci Internetu.

Vzhledem k tomu, že jedna relace může podporovat několik připojení `OnStatusCallback` (které během své životnosti mohou provádět mnoho různých odlišných operací), potřebuje mechanismus k identifikaci každé změny stavu s určitým připojením nebo transakcí. Tento mechanismus je poskytován parametrem ID kontextu, který je dán mnoha členským funkcím ve třídách podpory WinInet. Tento parametr je vždy typu **DWORD** a je vždy pojmenován *dwContext*.

Kontext přiřazený určitému objektu Sítě Internet slouží pouze k `OnStatusCallback` identifikaci `CInternetSession` aktivity, kterou objekt způsobuje v členu objektu. Volání přijímá `OnStatusCallback` několik parametrů; Tyto parametry společně sdělit aplikaci, jaký pokrok bylo dosaženo pro které transakce a připojení.

Při vytváření `CInternetSession` objektu můžete zadat parametr *dwContext* konstruktoru. `CInternetSession`sám nepoužívá ID kontextu; místo toho předá ID kontextu na všechny objekty odvozené **InternetConnection,** které explicitně získat vlastní ID kontextu. Na druhé `CInternetConnection` straně tyto objekty předá `CInternetFile` ID kontextu spolu s objekty, které vytvoří, pokud není explicitně zadat jiné ID kontextu. Pokud na druhé straně zadáte vlastní konkrétní ID kontextu, objekt a jakákoli práce, kterou provede, budou přidruženy k tomuto ID kontextu. ID kontextu můžete použít k určení, jaké informace o `OnStatusCallback` stavu jsou uvedeny ve vaší funkci.

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a>Zobrazení informací o průběhu při přenosu souborů

Pokud například napíšete aplikaci, která vytvoří připojení k serveru FTP ke čtení souboru a také se připojí `CInternetSession` k `CInternetConnection` serveru HTTP, abyste `CFtpSession` získali webovou `CHttpSession`stránku, budete mít objekt, dva objekty (jeden by byl a druhý a ) a dva `CInternetFile` objekty (jeden pro každé připojení). Pokud jste použili výchozí hodnoty pro parametry *dwContext,* nebude `OnStatusCallback` možné rozlišovat mezi vyvolání, které označují průběh připojení FTP a vyvolání, které označují průběh připojení HTTP. Pokud zadáte *dwContext* ID, které můžete později otestovat v aplikaci `OnStatusCallback`, budete vědět, která operace vygenerovala zpětné volání.

## <a name="see-also"></a>Viz také

[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)
