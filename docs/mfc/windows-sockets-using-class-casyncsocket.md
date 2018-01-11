---
title: "Windows Sockets: Použití třídy CAsyncSocket | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CAsyncSocket
dev_langs: C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 41a1bf9e7b162ecfe9724f22996f8883d95cce72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets – použití třídy CAsyncSocket
Tento článek vysvětluje, jak používat třídu [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Upozorňujeme, že tato třída zapouzdří rozhraní API systému Windows Sockets na velmi nízké úrovni. `CAsyncSocket`je pro používané programátory, kteří síťové komunikace podrobně znát, ale chcete pohodlí zpětných volání pro oznámení o události sítě. Podle této předpokladů, tento článek obsahuje pouze základní instrukcí. Měli byste pravděpodobně zvážit použití `CAsyncSocket` Pokud má Windows Sockets snadnou práci s několika síťových protokolů v aplikaci MFC, ale nechcete vzdát flexibilitu. Může také cítíte, že můžete získat lepší efektivitu programování další komunikace přímo sami, než jste může pomocí obecnější alternativní modelu třídy `CSocket`.  
  
 `CAsyncSocket`je popsána v *odkaz knihovny MFC*. Visual C++ také poskytuje specifikace rozhraní Windows Sockets, umístěný ve Windows SDK. Podrobnosti jsou ponechána na vás. Visual C++ neposkytuje ukázkovou aplikaci pro `CAsyncSocket`.  
  
 Pokud nejsou vysoce dobrou síťové komunikace a chcete jednoduchým řešením, použijte třídu [CSocket](../mfc/reference/csocket-class.md) s `CArchive` objektu. V tématu [Windows Sockets: použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) Další informace.  
  
 Tento článek se zabývá:  
  
-   Vytváření a používání `CAsyncSocket` objektu.  
  
-   [Vaše odpovědnosti s CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>Vytváření a používání objekt CAsyncSocket  
  
#### <a name="to-use-casyncsocket"></a>Chcete-li použít CAsyncSocket  
  
1.  Vytvořit [CAsyncSocket](../mfc/reference/casyncsocket-class.md) objektu a použít objekt k vytvoření základní **SOKETU** zpracování.  
  
     Vytvoření soketu následující MFC dvoufázová konstrukce.  
  
     Příklad:  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     -nebo-  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     Vytvoří první konstruktor výše `CAsyncSocket` objektu v zásobníku. Druhý konstruktor vytvoří `CAsyncSocket` v haldě. První [vytvořit](../mfc/reference/casyncsocket-class.md#create) volání výše používá výchozí hodnoty parametrů se vytvořit soket datového proudu. Druhý **vytvořit** volání vytvoří datagram soketu se zadaný port a adresa. (Můžete použít buď **vytvořit** verze pomocí některé z metod konstrukce.)  
  
     Parametry, které chcete **vytvořit** jsou:  
  
    -   "port": krátké celé číslo.  
  
         Pro server soketu je nutné určit port. Pro klienta soket obvykle přijmout výchozí hodnota tohoto parametru, která umožní Windows Sockets vyberte port.  
  
    -   Typ soketu: **SOCK_STREAM** (výchozí) nebo **SOCK_DGRAM**.  
  
    -   Soket "adresa, například"ftp.microsoft.com"nebo"128.56.22.8"".  
  
         Toto je vaše adresa Internet Protocol (IP) v síti. Bude pravděpodobně vždy spoléhají na výchozí hodnotu tohoto parametru.  
  
     Podmínky "port" a "adresa soketu" jsou vysvětlené v [Windows Sockets: porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Pokud klient soketu se připojit k serveru objekt soketu soketu, pomocí [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).  
  
     -nebo-  
  
     Pokud soketu je server, nastavte časový limit soketu aby začal přijímat (s [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) pro pokusy o připojení z klienta. Po přijetí požadavku na připojení, přijměte je [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
     Po přijetí připojení, můžete provést úkoly, jako je ověřování hesla.  
  
    > [!NOTE]
    >  **Přijmout** – členská funkce trvá odkaz na nový, prázdný `CSocket` objektu jako její parametr. Je nutné vytvořit tento objekt před voláním **přijmout**. Pokud se tento objekt soketu se ocitne mimo obor, připojení se ukončí. Nevolejte **vytvořit** pro tento nový objekt soketu. Příklad najdete v článku [Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md).  
  
3.  Provádění komunikace s další sockets voláním `CAsyncSocket` objektu členské funkce, které zapouzdřují funkce rozhraní Windows Sockets API.  
  
     Najdete v části Windows Sockets specifikaci a třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md) v *odkaz knihovny MFC*.  
  
4.  Zrušení `CAsyncSocket` objektu.  
  
     Pokud jste vytvořili objekt soketu se v zásobníku, jeho destruktor je volána, když obsahující funkce ocitne mimo rozsah. Pokud jste vytvořili objekt soketu v haldě, pomocí **nové** operátor, je zodpovědná za použití **odstranit** operátor odstranění objektu.  
  
     Volání destruktoru objektu [Zavřít](../mfc/reference/casyncsocket-class.md#close) – členská funkce před zničení objektu.  
  
 Příklad toto pořadí v kódu (ve skutečnosti pro `CSocket` objektu), najdete v části [Windows Sockets: pořadí operací](../mfc/windows-sockets-sequence-of-operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a>Vaše odpovědnosti s CAsyncSocket  
 Když vytvoříte objekt třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), objekt zapouzdří Windows **SOKETU** zpracování a poskytuje operací na popisovače. Při použití `CAsyncSocket`, musí řešit všechny problémy, může čelí Pokud přímo pomocí rozhraní API. Příklad:  
  
-   "Blokování" scénáře.  
  
-   Byte pořadí rozdíly mezi odesílajícím a přijímajícím počítače.  
  
-   Převod mezi kódování Unicode a vícebajtové znakové sady (MBCS) řetězce.  
  
 Definice tyto podmínky a další informace naleznete v tématu [Windows Sockets: blokování](../mfc/windows-sockets-blocking.md), [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: převádění řetězců](../mfc/windows-sockets-converting-strings.md) .  
  
 Přes všechny tyto problémy třídy **CAsycnSocket** může být správnou volbou pro vás, pokud vaše aplikace vyžaduje flexibilitu a řízení můžete získat. Pokud ne, měli byste zvážit použití třídy `CSocket` místo. `CSocket`Skryje velké množství informací od vás: it čerpadel Windows zpráv během blokování volání a získáte přístup k `CArchive`, který spravuje rozdíly pořadí bajtů a převod řetězce pro vás.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

