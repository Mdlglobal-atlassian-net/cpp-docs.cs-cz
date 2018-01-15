---
title: "Windows Sockets: Pořadí bajtů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c25a7b2c8240531e1d778d6a119f857032423db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Pořadí bajtů
V tomto článku a dvě doprovodné články vysvětlují několik problémů v rozhraní Windows Sockets programování. Tento článek se zabývá pořadí bajtů. Další problémy, které jsou popsané v článcích: [Windows Sockets: blokování](../mfc/windows-sockets-blocking.md) a [Windows Sockets: převádění řetězců](../mfc/windows-sockets-converting-strings.md).  
  
 Pokud používáte nebo odvozena od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset řešení těchto problémů. Pokud používáte nebo odvozena od třídy [CSocket](../mfc/reference/csocket-class.md), spravuje MFC za vás.  
  
## <a name="byte-ordering"></a>Pořadí bajtů  
 Jiný počítač architektury někdy ukládat data pomocí různých bajtů objednávky. Počítače založené na Intel například ukládat data v obráceném pořadí počítače Macintosh (Motorola). Pořadí bajtů Intel, nazývá "little Endian," je také zpětného "big Endian" pořadí standardní síti. Následující tabulka vysvětluje tyto podmínky.  
  
### <a name="big--and-little-endian-byte-ordering"></a>Big - a Little Endian pořadí bajtů  
  
|Pořadí bajtů|Význam|  
|-------------------|-------------|  
|Big Endian|Nejvýznamnější bajt je v levém konci slova.|  
|Little Endian|Na pravém konci slovo je nejvýznamnější bajt.|  
  
 Obvykle nemusíte si dělat starosti o převod pořadí bajtů pro data, která můžete odesílat a přijímat přes síť, ale existují situace, ve kterých je nutné převést objednávky bajtů.  
  
## <a name="when-you-must-convert-byte-orders"></a>Když je nutné převést objednávky bajtů  
 Budete muset převést objednávky bajtů v následujících situacích:  
  
-   Předáváte informace, které musí být interpretovat sítě, nikoli data, která při odesílání do jiného počítače. Například může předat porty a adresy, které musíte pochopit sítě.  
  
-   Aplikace serveru, se kterým budou komunikovat není aplikace knihovny MFC (a pro něj nemáte zdrojový kód). Toto volání pro převody pořadí bajtů, pokud dva počítače nesdílejí stejný pořadí bajtů.  
  
## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Pokud není nutné převést objednávky bajtů  
 Chcete-li předejít práci při převádění objednávek bajtů v následujících situacích:  
  
-   Počítače na obou koncích můžete souhlas nechcete Prohodit bajtů a oba počítače používat stejné pořadí bajtů.  
  
-   Server, které komunikují pomocí je aplikace knihovny MFC.  
  
-   Máte zdrojový kód serveru, který komunikujete, takže se dá explicitně zjistit, zda je nutné převést objednávky bajtů, nebo ne.  
  
-   Server s knihovnou MFC můžete portu. Toto je poměrně snadné provést a výsledkem je obvykle menší a rychlejší kódu.  
  
 Práce s [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musí všechny potřebné pořadí bajtů převody spravovat sami. Windows Sockets standardizuje pořadí bajtů "big Endian" modelu a poskytuje funkce pro převod mezi tomto pořadí a ostatní uživatele. [CArchive](../mfc/reference/carchive-class.md), ale který můžete použít s [CSocket](../mfc/reference/csocket-class.md), používá opačném pořadí ("little Endian"), ale `CArchive` postará podrobnosti o pořadí bajtů převody za vás. Pomocí této standardní řazení v aplikacích, nebo pomocí funkce pro převod Windows Sockets pořadí bajtů, můžete nastavit kód víc přenosného.  
  
 Ideálním případem použití soketů knihovny MFC je, když vytváříte obě strany komunikace: používáte knihovnu MFC na obou koncích. Pokud píšete aplikaci, která budou komunikovat s mimo MFC aplikace, jako je FTP server, budete pravděpodobně muset spravovat vzájemná záměna bajtů sami před předat data do archivu objekt, pomocí rutiny Windows Sockets převodu **ntohs**, **ntohl**, **htons**, a **htonl**. Příkladem těchto funkcí používaných v komunikaci s aplikací mimo MFC se zobrazí později v tomto článku.  
  
> [!NOTE]
>  Při druhém konci komunikace není aplikace knihovny MFC, můžete také musí předejít streamování objekty C++ odvozené z `CObject` na vašem archivu protože příjemce nebude moci zpracovat je. Přečtěte si poznámku v [Windows Sockets: použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md).  
  
 Další informace o bajtů objednávky najdete v rozhraní Windows Sockets specifikaci, k dispozici v sadě Windows SDK.  
  
## <a name="a-byte-order-conversion-example"></a>V příkladu převod pořadí bajtů  
 Následující příklad ukazuje funkci serializace `CSocket` objekt, který používá archivu. Kromě toho ilustruje pomocí funkce pro převod pořadí bajtů v rozhraní Windows Sockets API.  
  
 V tomto příkladu představuje scénář, ve kterém jsou zápisu klienta, který komunikuje s aplikace mimo MFC server, pro které nemáte přístup ke zdrojovému kódu. V tomto scénáři musí předpokládat, že server mimo MFC pomocí standardního síťového pořadí bajtů. Naproti tomu klientské aplikace MFC používá `CArchive` objektu s `CSocket` objekt, a `CArchive` používá pořadí bajtů "little Endian", je opakem standardní síti.  
  
 Předpokládejme, že mimo MFC serveru, pomocí kterého budete komunikovat má stanoveného protokolu pro zprávy paket takto:  
  
 [!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]  
  
 V MFC podmínky to by být vyjádřena takto:  
  
 [!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]  
  
 V jazyce C++ `struct` je v podstatě totéž jako třída. `Message` Struktura může mít členské funkce, jako `Serialize` členské funkce deklarována výše. `Serialize` – Členská funkce může vypadat například takto:  
  
 [!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]  
  
 Tento příklad volá pro převody pořadí bajtů dat, protože došlo k neshodě zrušte mezi pořadí bajtů mimo MFC serverové aplikace na jeden element end a `CArchive` použít v klientské aplikace MFC na druhém konci. Tento příklad znázorňuje několik funkcí převod pořadí bajtů, které poskytuje Windows Sockets. Následující tabulka popisuje tyto funkce.  
  
### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets – funkce pro převod pořadí bajtů  
  
|Funkce|Účel|  
|--------------|-------------|  
|**ntohs**|Převod množství 16bitové pořadí bajtů sítě na hostiteli pořadí bajtů (big Endian k little Endian).|  
|**ntohl**|Převod množství 32-bit pořadí bajtů sítě na hostiteli pořadí bajtů (big Endian k little Endian).|  
|**Htons**|Převod množství 16bitové pořadí bajtů hostitele na síťovém pořadí bajtů (little Endian na big Endian).|  
|**Htonl**|Převod množství 32-bit pořadí bajtů hostitele na síťovém pořadí bajtů (little Endian na big Endian).|  
  
 Jiný bod v tomto příkladu je, když je aplikace soketu na druhém konci komunikace mimo MFC aplikace, musí vyhýbat se něco podobného jako následujícím způsobem:  
  
 `ar << pMsg;`  
  
 kde `pMsg` ukazatel na objekt C++ odvozené od třídy `CObject`. Tím se pošle, že doplňující informace MFC související s objekty a server nebude moci pracovat, jako kdyby šlo o aplikace knihovny MFC.  
  
 Další informace naleznete v tématu:  
  
-   [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)

