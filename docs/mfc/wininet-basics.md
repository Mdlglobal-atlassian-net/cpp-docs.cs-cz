---
title: "WinInet – základy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0598b131305684e9134a223fd599a8b642bf6da7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wininet-basics"></a>WinInet – základy
WinInet můžete přidat podporu FTP ke stažení a ukládání souborů z v rámci vaší aplikace. Můžete přepsat [onstatuscallback –](../mfc/reference/cinternetsession-class.md#onstatuscallback) a použít `dwContext` parametr zadat informace o průběhu pro uživatele, jsou pro hledání a stahování souborů.  
  
 Tento článek obsahuje následující témata:  
  
-   [Vytvořit velmi jednoduchý prohlížeč](#_core_create_a_very_simple_browser)  
  
-   [Stažení webové stránky](#_core_download_a_web_page)  
  
-   [FTP souboru](#_core_ftp_a_file)  
  
-   [Načtení adresáře Gopher](#_core_retrieve_a_gopher_directory)  
  
-   [Zobrazit informace o průběhu při přenosu souborů](#_core_display_progress_information_while_transferring_files)  
  
 Úryvky kódu níže ukazují, jak vytvořit jednoduchý prohlížeč, stáhněte na webové stránce, FTP souboru a vyhledejte soubor gopher. Nejsou určeny jako příklady úplný a ne všechny obsahovat výjimek.  
  
 Další informace o WinInet najdete v tématu [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md).  
  
##  <a name="_core_create_a_very_simple_browser"></a>Vytvořit velmi jednoduchý prohlížeč  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a>Stažení webové stránky  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a>FTP souboru  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a>Načtení adresáře Gopher  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]  
  
## <a name="use-onstatuscallback"></a>Onstatuscallback – použití  
 Při používání tříd WinInet, můžete použít [onstatuscallback –](../mfc/reference/cinternetsession-class.md#onstatuscallback) členem vaší aplikace [CInternetSession](../mfc/reference/cinternetsession-class.md) objekt, který chcete načíst informace o stavu. Pokud odvozujete vlastní `CInternetSession` objektu, přepsání `OnStatusCallback`a povolit stav zpětná volání, zavolá MFC vaší `OnStatusCallback` funkce s informace o průběhu o všechny aktivity v této relaci Internet.  
  
 Protože jedné relace může podporovat několik připojení, (a které průběhu své životnosti, může provedení mnoha různých různých operací), `OnStatusCallback` musí mechanismus k identifikaci každé změně stavu s konkrétní připojení nebo transakci. Tento mechanismus jsou poskytovány na řadu členské funkce ve podpůrných tříd WinInet parametru ID kontextu. Tento parametr je vždy typu `DWORD` a je vždy s názvem `dwContext`.  
  
 Kontext přiřazen určitý objekt Internet slouží pouze k identifikaci aktivity objekt způsobí, že v `OnStatusCallback` členem `CInternetSession` objektu. Volání `OnStatusCallback` přijímá několik parametrů, tyto parametry spolupracují oznámit aplikaci, které nebyly pro jaké transakce a připojení.  
  
 Při vytváření `CInternetSession` objekt, můžete zadat `dwContext` parametr konstruktoru. `CInternetSession`samotný nepoužívá ID kontextu; Místo toho předává ID kontextu k žádné **InternetConnection**-odvozené objekty, které explicitně Nezískávat vlastní ID kontextu. V vypnout, ty `CInternetConnection` objekty předá ID kontextu společně na `CInternetFile` objekty vytvoří Pokud nezadáte explicitně kontextu jiné ID. Pokud na druhé straně určíte vlastní ID konkrétní kontextu, objekt a všechny pracovní bude přidružen ID tohoto kontextu. Kontext ID můžete použít k identifikaci, jaké informace o stavu je ohledem v vaší `OnStatusCallback` funkce.  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a>Zobrazit informace o průběhu při přenosu souborů  
 Například pokud píšete aplikaci, která vytvoří připojení k serveru FTP pro čtení souboru a také se připojí k serveru HTTP získat na webové stránce, budete mít `CInternetSession` objektu, dva `CInternetConnection` objekty (jeden by **CFtpSession** a dalších by **CHttpSession**) a dvě `CInternetFile` objekty (jeden pro každé připojení). Pokud jste použili výchozí hodnoty pro `dwContext` parametrů, nebude možné rozlišit mezi `OnStatusCallback` volání, které indikují průběh pro připojení FTP a volání, které indikují průběh pro připojení protokolu HTTP. Pokud zadáte `dwContext` ID, které lze později otestovat v `OnStatusCallback`, budete vědět, kterou operaci generované zpětné volání.  
  
## <a name="see-also"></a>Viz také  
 [Základy internetového programování MFC](../mfc/mfc-internet-programming-basics.md)   
 [Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)

