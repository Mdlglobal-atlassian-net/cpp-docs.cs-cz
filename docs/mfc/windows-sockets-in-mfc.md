---
title: Windows Sockets v prostředí MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84fc25ab6515b22fa647b3cc32833c791b59f2b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385509"
---
# <a name="windows-sockets-in-mfc"></a>Windows sockets v prostředí MFC
> [!NOTE]
>  MFC podporuje Windows Sockets 1, ale nepodporuje [rozhraní Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673). Windows Sockets 2 nejdřív dodávané se systémem Windows 98 a je verze systému Windows 2000.  
  
 MFC poskytuje dva modely pro zápis programy komunikaci sítě s Windows Sockets, součástí dvě třídy MFC. Tento článek popisuje tyto modely a další podrobnosti MFC sokety podpory. "Soket" je koncový bod komunikace: objekt, pomocí kterého aplikace komunikuje s jinými aplikacemi Windows Sockets v síti.  
  
 Informace o rozhraní Windows Sockets, včetně vysvětlení konceptu soketu, najdete v části [Windows Sockets: pozadí](../mfc/windows-sockets-background.md).  
  
##  <a name="_core_sockets_programming_models"></a> Modely programování soketů  
 Programovací modely dva Windows Sockets MFC podporuje následující třídy:  
  
-   `CAsyncSocket`  
  
     Tato třída zapouzdří rozhraní Windows Sockets API. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) je pro programátory, kteří vědět síťové programování a chcete flexibilitu programování přímo na sokety rozhraní API, ale také chcete pohodlím, které představuje funkce zpětného volání pro oznámení o události sítě. Než balení sockets v objektově orientované formuláře pro použití v jazyce C++, je jenom další abstrakce, kterou tato třída poskytuje převodu některé zprávy související s soketu Windows zpětných volání. Další informace najdete v tématu [Windows Sockets: oznámení soketů](../mfc/windows-sockets-socket-notifications.md).  
  
-   `CSocket`  
  
     Tato třída odvozená z `CAsyncSocket`, poskytuje vyšší úrovni abstrakce pro práci s sockets prostřednictvím knihovny MFC [CArchive](../mfc/reference/carchive-class.md) objektu. Soket pomocí archiv výrazně se podobá pomocí knihovny MFC souboru serializace protokolu. Díky tomu je jednodušší než `CAsyncSocket` modelu. [CSocket](../mfc/reference/csocket-class.md) dědí z mnoha členské funkce `CAsyncSocket` zapouzdřují rozhraní API systému Windows Sockets; bude mít používat některé z těchto funkcí a pochopit obecně programování soketů. Ale `CSocket` spravuje mnoho aspektů komunikaci, která budete muset provést sami pomocí nezpracovaná rozhraní API nebo třída `CAsyncSocket`. Co je nejdůležitější – `CSocket` poskytuje blokování (s pozadí zpracování zpráv systému Windows), které je nezbytné pro synchronní operace `CArchive`.  
  
 Vytváření a používání `CSocket` a `CAsyncSocket` objektů je popsaná v [Windows Sockets: použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) a [Windows Sockets: použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).  
  
##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets – knihovny DLL  
 Windows Sockets dynamické knihovny (DLL), zadejte operační systémy Microsoft Windows. Visual C++ poskytuje odpovídající hlavičkových souborů a knihoven a specifikace rozhraní Windows Sockets.  
  
 Další informace o rozhraní Windows Sockets najdete v tématu:  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
-   [Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets: Posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md)  
  
-   [Windows Sockets: Příklady soketů využívajících archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)  
  
-   [Windows Sockets: Oznámení soketů](../mfc/windows-sockets-socket-notifications.md)  
  
-   [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)  
  
-   [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)  
  
-   [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)  
  
-   [Windows Sockets: Porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní Windows Sockets](../mfc/windows-sockets.md)

