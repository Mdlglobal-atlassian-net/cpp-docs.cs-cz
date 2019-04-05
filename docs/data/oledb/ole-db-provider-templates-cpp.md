---
title: Šablony zprostředkovatele OLE DB (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 793aa08630ec92f99c33c2a4f3688e78630a6c58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027469"
---
# <a name="ole-db-provider-templates-c"></a>Šablony zprostředkovatele OLE DB (C++)

OLE DB je důležitou součástí strategie Microsoft univerzální přístup k datům. OLE DB návrh umožňuje přístup k vysoce výkonné datům z libovolného zdroje dat. Žádná tabulková data lze zobrazit pomocí technologie OLE DB bez ohledu na to, zda pochází z databáze. Flexibilita vám obrovské množství výkonu.

Jak je vysvětleno v [OLE DB příjemci a zprostředkovatelé](../../data/oledb/ole-db-consumers-and-providers.md), používá koncept příjemci a zprostředkovatelé technologie OLE DB. Příjemce provede žádostí o poskytování dat; zprostředkovatel vrací data ve formátu tabulky příjemci. Z hlediska programovací nejdůležitější důsledkem tohoto modelu je, že zprostředkovatel musí implementovat jakékoli volání, které můžete provést příjemce.

## <a name="what-is-a-provider"></a>Co je poskytovatel?

Zprostředkovatele OLE DB je sada COM objektů, které slouží k volání rozhraní z objektu příjemce, přenos dat ve formátu tabulky z trvalý zdroj (označované jako úložiště dat) příjemci.

Zprostředkovatelé můžou být jednoduché nebo složité. Zprostředkovatel můžete podpořit minimální nároky na kvalitu zprostředkovatele plnohodnotném produkčním nebo funkce implementovat více rozhraní. Zprostředkovatele může vrátit tabulku povolit klienta k určení formátu tabulky a provádění operací na těchto datech.

Každý poskytovatel implementuje standardní sadu objektů modelu COM pro zpracování žádosti z klienta pomocí standardní smyslu, že všechny příjemce technologie OLE DB můžou přistupovat k datům z libovolného poskytovatele, bez ohledu na jazyk (třeba C++ a Basic).

Každý objekt modelu COM obsahuje několik rozhraní, z nichž některé jsou vyžadovány a některé z nich jsou volitelné. Implementací rozhraní povinné zaručuje zprostředkovatele minimální úroveň funkčnosti (volaná dodržování předpisů), který by měl být možné použít libovolného klienta. Poskytovatel může implementovat volitelné rozhraní k poskytnutí dalších funkcí. [OLE DB Architektura šablon zprostředkovatele](../../data/oledb/ole-db-provider-template-architecture.md) popisuje podrobně těchto rozhraní. Klient musí vždy volat `QueryInterface` k zjištění, zda poskytovatel podporuje dané rozhraní.

## <a name="ole-db-specification-level-support"></a>Úroveň podpory specifikaci OLE DB

Šablony zprostředkovatele OLE DB podporují specifikaci verze 2.7 OLE DB. Šablony zprostředkovatele OLE DB můžete implementovat kompatibilní poskytovatel úroveň 0. `Provider` Vzorku, například používá šablony k implementaci serveru non příkaz, který provede příkaz DOS DIR k dotazování systému souborů. `Provider` Ukázka vrátí informace o adresáře v sadě řádků, což je standardní mechanismus pro vrácení tabulkových dat OLE DB.

Nejjednodušší typ zprostředkovatele nepodporuje šablony technologie OLE DB je poskytovatel jen pro čtení s žádné příkazy. Zprostředkovatelé s příkazy jsou také podporovány, jako jsou funkce záložek a čtení a zápisu. Čtení a zápis poskytovatele můžete implementovat psaním dalšího kódu. Aktuální verze nepodporuje dynamické sady řádků a transakce, ale pokud chcete, můžete je přidat.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Když je potřeba k vytvoření zprostředkovatele OLE DB?

Není vždy nutné k vytvoření vlastního zprostředkovatele; Společnost Microsoft poskytuje několik předem zabalených standardní zprostředkovatelů v **vlastnosti propojení dat** dialogové okno v jazyce Visual C++. Hlavním důvodem k vytvoření zprostředkovatele OLE DB je využívat strategie univerzální přístup k datům. Mezi výhody tak patří:

- Přístup k datům pomocí libovolného jazyka, jako je například C++, Basic a Visual Basic Scripting Edition. Umožňuje různé programátorům v organizaci přístup ke stejným datům stejně, bez ohledu na to, jaký jazyk používají.

- Otevřete data k jiným zdrojům dat, jako je například SQL Server, Excel a Access. To může být užitečné, pokud chcete přenos dat mezi různými formáty.

- Účasti v operacích zdrojů dat napříč (heterogenní). To může být účinný způsob datových skladů. S použitím zprostředkovatelů OLE DB, můžete ponechat data v nativním formátu a mít pořád povolený přístup v rámci jednoduché operace.

- Přidává další funkce k datům, jako je zpracování dotazů.

- Zvýšení výkonu přístup k datům pomocí řízení, jak je zpracováván.

- Zvýšení odolnosti. Pokud máte specifická vlastní data formátu přístup k této pouze jeden programátora, vystavujete se riziku. Pomocí zprostředkovatele OLE DB, můžete otevřít tento vlastnický formát všechny programátorům.

## <a name="read-only-and-updatable-providers"></a>Jen pro čtení a aktualizovatelní zprostředkovatelé

Poskytovatelé může značně lišit složitost a funkce. Je užitečné kategorizovat zprostředkovatele na zprostředkovatele jen pro čtení a aktualizovatelní zprostředkovatelé:

- Visual C++ 6.0 podporuje pouze zprostředkovatelé jen pro čtení. [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md) popisuje, jak vytvořit zprostředkovatele pouze pro čtení.
- Jazyk Visual C++ podporuje aktualizovatelné zprostředkovatele, které můžete aktualizovat (zápis do) úložiště. Informace o aktualizovatelní zprostředkovatelé najdete v tématu [vytvoření aktualizovatelného zprostředkovatele](../../data/oledb/creating-an-updatable-provider.md); [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ukázka je příkladem aktualizovatelného zprostředkovatele.

Další informace naleznete v tématu:

- [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [OLE DB – programování](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Viz také:

[Přístup k datům](../data-access-in-cpp.md)<br/>
[Dokumentace k sadě SDK technologie OLE DB](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Referenční informace pro OLE DB programátory](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
