---
title: 'Windows Sockets: Použití soketů s archivy | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7ad4e5b94403582f9073e4d3bd3542f8aa75d08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Použití soketů s archivy
Tento článek popisuje [CSocket programovací model](#_core_the_csocket_programming_model). Třída [CSocket](../mfc/reference/csocket-class.md) poskytuje podporu soketu na vyšší úrovni abstrakce než třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` používá verzi protokolu serializace MFC k předávání dat do a z objekt soketu prostřednictvím knihovny MFC [CArchive](../mfc/reference/carchive-class.md) objektu. `CSocket` poskytuje blokování (při správě zpracování na pozadí zpráv systému Windows) a poskytuje přístup k `CArchive`, který spravuje mnoho aspektů komunikaci, která budete muset provést sami pomocí nezpracovaná rozhraní API nebo třída `CAsyncSocket`.  
  
> [!TIP]
>  Třídu můžete použít `CSocket` samostatně jako pohodlnější verze `CAsyncSocket`, ale je nejjednodušší programovací model použití `CSocket` s `CArchive` objektu.  
  
 Další informace o tom, jak funguje implementace sokety s archivy najdete v tématu [Windows Sockets: jak sokety s archivy pracovní](../mfc/windows-sockets-how-sockets-with-archives-work.md). Příklad kódu, najdete v části [Windows Sockets: pořadí operací](../mfc/windows-sockets-sequence-of-operations.md) a [Windows Sockets: příklad z Sockets pomocí archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md). Informace o některých funkcích získáte vaše vlastní třídy odvozené z tříd soketů najdete v tématu [Windows Sockets: odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
> [!NOTE]
>  Pokud píšete aplikace MFC klienta ke komunikaci se servery zavedených (mimo MFC), Neodesílat objekty C++ prostřednictvím archivu. Pokud je server aplikace knihovny MFC, který rozumí druhy objektů, které chcete odeslat, nebude moci přijímat a deserializaci objektů. Související informace o subjektu komunikaci s aplikacemi mimo MFC si také najdete v článku [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md).  
  
##  <a name="_core_the_csocket_programming_model"></a> CSocket modelu programování  
 Použití `CSocket` objekt zahrnuje vytvoření a přiřazení společně několik objekty tříd MFC. V níže uvedeném obecné postupu je každý krok provedenou soketu serveru a klienta soketu, s výjimkou kroku 3, ve kterém každý typ soketu vyžaduje jinou akci.  
  
> [!TIP]
>  V době běhu je serverová aplikace obvykle spustí nejprve připravené a "naslouchá", pokud klientská aplikace snaží o připojení. Pokud server není připraven, když se klient pokusí o připojení, obvykle vyžadují uživatelská aplikace a zkuste to znovu později připojení.  
  
#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Nastavení komunikace mezi soketu serveru a klienta soketů  
  
1.  Vytvořit [CSocket](../mfc/reference/csocket-class.md) objektu.  
  
2.  Použít objekt k vytvoření základní **SOKETU** zpracování.  
  
     Pro `CSocket` objektu klienta za normálních okolností byste měli používat výchozí parametry, které chcete [vytvořit](../mfc/reference/casyncsocket-class.md#create), pokud potřebujete datagram soketu. Pro `CSocket` objekt serveru, je nutné zadat port v **vytvořit** volání.  
  
    > [!NOTE]
    >  `CArchive` nefunguje s sokety datagramů. Pokud chcete použít `CSocket` pro soket datagram, musíte použít třídu, jako byste použili `CAsyncSocket`, která je bez archivu. Protože datagramy nespolehlivé (není zaručené doručení a může se znovu nebo mimo pořadí), nejsou kompatibilní s serializace prostřednictvím archivu. Očekáváte serializace operace dokončit spolehlivě a v pořadí. Pokud se pokusíte použít `CSocket` s `CArchive` objekt pro datagram, kontrolní výrazy MFC selže.  
  
3.  Pokud soketu je klient, zavolejte [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) objekt soketu se připojit k serveru soketu.  
  
     -nebo-  
  
     Pokud soket serveru, volání [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) zahájíte naslouchání pro pokusy o připojení z klienta. Po přijetí požadavku na připojení, přijměte voláním [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
    > [!NOTE]
    >  **Přijmout** – členská funkce trvá odkaz na nový, prázdný `CSocket` objektu jako její parametr. Je nutné vytvořit tento objekt před voláním **přijmout**. Pokud se tento objekt soketu se ocitne mimo obor, připojení se ukončí. Nevolejte **vytvořit** pro tento nový objekt soketu.  
  
4.  Vytvoření [CSocketFile](../mfc/reference/csocketfile-class.md) objektu přidružení `CSocket` objektu s ním.  
  
5.  Vytvoření [CArchive](../mfc/reference/carchive-class.md) objekt pro načítání (příjem) nebo ukládání dat (odesílajícím). Je přidružen archivu `CSocketFile` objektu.  
  
     Mějte na paměti, `CArchive` nefunguje s sokety datagramů.  
  
6.  Použití `CArchive` objektu k předávání dat mezi klientem a serverem sokety.  
  
     Mějte na paměti, že danou `CArchive` objekt přesouvá data jenom v jednom směru: buď pro načítání (příjem) nebo ukládání (odesílajícím). V některých případech budete používat dvě `CArchive` objekty: jeden pro odesílání dat, druhý pro příjem potvrzování.  
  
     Po přijetí připojení a nastavení archivu, můžete provést úkoly, jako je ověřování hesla.  
  
7.  Destroy – archiv, soubor soketu a objekty soketu.  
  
    > [!NOTE]
    >  Třída `CArchive` poskytuje `IsBufferEmpty` – členská funkce pro použití s třídou `CSocket`. Pokud vyrovnávací paměť obsahuje více datových zpráv, například budete muset opakovat až do všechny z nich se čtou a vyrovnávací paměť je zrušeno. Jinak hodnota může být po neomezenou dobu odložené další oznámení, že se data k přijetí. Použití `IsBufferEmpty` , aby zajistil, že je načíst všechna data.  
  
 Článek [Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md) znázorňuje obou stranách tohoto procesu se ukázkový kód.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket::Create](../mfc/reference/csocket-class.md#create)

