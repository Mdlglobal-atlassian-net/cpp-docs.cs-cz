---
title: Wininet – základy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ca2eab519cdfa3140d40adfd83070976dcc965
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435646"
---
# <a name="wininet-basics"></a>WinInet – základy

Wininet – slouží k přidání podpory protokolu FTP ke stažení a nahrání souborů z v rámci vaší aplikace. Můžete přepsat [onstatuscallback –](../mfc/reference/cinternetsession-class.md#onstatuscallback) a použít *dwContext* parametr můžete uživatelům poskytnout informace o průběhu, jak vyhledat a stáhnout soubory.

Tento článek obsahuje následující témata:

- [Vytvořit velmi jednoduchý prohlížeč](#_core_create_a_very_simple_browser)

- [Stáhněte si na webové stránce](#_core_download_a_web_page)

- [Soubor protokolu FTP](#_core_ftp_a_file)

- [Načtení adresáře Gopher](#_core_retrieve_a_gopher_directory)

- [Zobrazení informací o průběhu při přenosu souborů](#_core_display_progress_information_while_transferring_files)

Ukázky kódu níže ukazují, jak vytvořit jednoduchý prohlížeč, stáhněte si na webové stránce, FTP souboru a vyhledejte soubor gopher. Nejsou určeny jako kompletní příklady a ne všechny obsahují zpracování výjimek.

Další informace o rozhraní WinInet, naleznete v tématu [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md).

##  <a name="_core_create_a_very_simple_browser"></a> Vytvořit velmi jednoduchý prohlížeč

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

##  <a name="_core_download_a_web_page"></a> Stáhněte si na webové stránce

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

##  <a name="_core_ftp_a_file"></a> Soubor protokolu FTP

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

##  <a name="_core_retrieve_a_gopher_directory"></a> Načtení adresáře Gopher

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>Onstatuscallback – použití

Když pomocí tříd WinInet, můžete [onstatuscallback –](../mfc/reference/cinternetsession-class.md#onstatuscallback) členem vaší aplikace [cinternetsession –](../mfc/reference/cinternetsession-class.md) objektu k načtení informací o stavu. Pokud odvozujete vlastní `CInternetSession` objektu, přepsat `OnStatusCallback`a povolit stav zpětná volání, knihovny MFC bude volat vaše `OnStatusCallback` funkce s informací o průběhu o všech aktivitách v této relaci Internet.

Protože jedné relace může podporovat několik připojení (a které průběhu své životnosti, může provést několika různých operací distinct) `OnStatusCallback` potřebuje mechanismus pro identifikaci každou změnu stavu připojení nebo transakce. Tento mechanismus je poskytována kontextový parametr ID k mnoha členských funkcí v třídách WinInet podpory. Tento parametr je vždy typu **DWORD** a je vždy pojmenováno *dwContext*.

Kontext přiřazené k určitému objektu Internet slouží pouze k identifikaci aktivity způsobí, že objekt v `OnStatusCallback` člena `CInternetSession` objektu. Volání `OnStatusCallback` přijímá několik parametrů; tyto parametry společně oznámit aplikaci, jaký pokrok pro připojení a transakce.

Když vytvoříte `CInternetSession` objektu, můžete zadat *dwContext* parametr konstruktoru. `CInternetSession` samotný nepoužívá ID kontextu; Místo toho předává ID kontextu k libovolné **InternetConnection**-odvozené objekty, které nejsou explicitně získat ID kontextu své vlastní. Následně bude ty `CInternetConnection` objekty předá ID kontextu podél k `CInternetFile` objekty vytvářejí, pokud není explicitně zadejte ID jiného kontextu. Pokud na druhé straně nezadáte vlastní ID konkrétní kontext, objektu a veškerou práci se bude spojená s ID tohoto kontextu. Kontext ID můžete použít k určení, jaké informace o stavu se dostane ve vaší `OnStatusCallback` funkce.

##  <a name="_core_display_progress_information_while_transferring_files"></a> Zobrazení informací o průběhu při přenosu souborů

Například, když zapíšete aplikaci, která vytvoří připojení k serveru FTP ke čtení souboru a také připojuje k serveru HTTP se získat na webové stránce, budete mít `CInternetSession` objektu, dvěma `CInternetConnection` objekty (jeden by `CFtpSession` a druhá bude `CHttpSession`) a dvě `CInternetFile` objekty (jeden pro každé připojení). Pokud jste použili výchozí hodnoty pro *dwContext* parametry, nebude možné rozlišit `OnStatusCallback` volání, které označují průběh připojení FTP a volání, které označují průběh Připojení HTTP. Pokud zadáte *dwContext* ID, které můžete později otestovat pro `OnStatusCallback`, budete vědět, jaké operace vytvořila zpětného volání.

## <a name="see-also"></a>Viz také

[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)

