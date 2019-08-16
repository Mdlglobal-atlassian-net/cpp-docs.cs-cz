---
title: Problémy s návrhem technologie OLE DB
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: b481d9948d3055247bd284ca794a0fa65905e21b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501347"
---
# <a name="ole-db-architectural-design-issues"></a>Problémy s návrhem technologie OLE DB

> [!NOTE]
> Průvodce příjemcem OLE DB ATL není v aplikaci Visual Studio 2019 a novějších k dispozici. Tuto funkci můžete přesto přidat ručně. Další informace najdete v tématu [Vytvoření příjemce bez použití Průvodce](creating-a-consumer-without-using-a-wizard.md).

Před spuštěním aplikace OLE DB je třeba vzít v úvahu následující problémy:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Jakou implementaci programování použijete k zápisu aplikace OLE DB?

Společnost Microsoft nabízí několik knihoven pro splnění této úlohy: OLE DB knihovny šablon, OLE DB atributů a nezpracované OLE DB rozhraní v sadě OLE DB SDK. K dispozici jsou také průvodci, které vám pomůžou napsat program. Tyto implementace jsou popsány v tématu [OLE DB šablony, atributy a další implementace](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>Potřebujete napsat vlastního poskytovatele?

Většina vývojářů nepotřebuje psát vlastního poskytovatele. Společnost Microsoft poskytuje několik poskytovatelů. Pokaždé, když vytvoříte datové připojení (například když do projektu přidáte příjemce pomocí **průvodce OLE DB příjemcem**), zobrazí se dialogové okno **Vlastnosti datového propojení** všech dostupných zprostředkovatelů registrovaných ve vašem systému. Pokud je jedno z poskytovatelů vhodné pro vaše vlastní datové úložiště a aplikace pro přístup k datům, nejjednodušší je použít jeden z nich. Pokud však vaše úložiště dat nesplňuje některé z těchto kategorií, je nutné vytvořit vlastního poskytovatele. Informace o vytváření zprostředkovatelů najdete v tématu [šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Jakou úroveň podpory potřebujete pro vašeho příjemce?

Někteří příjemci můžou být základní; jiné můžou být složité. Funkce objektů OLE DB je určena vlastnostmi. Když použijete **průvodce OLE DB příjemce ATL** k vytvoření příjemce nebo **Průvodce poskytovatelem databáze** pro vytvoření poskytovatele, nastaví příslušné vlastnosti objektu, které vám poskytnou standardní sadu funkcí. Nicméně pokud třídy příjemce nebo poskytovatele generované průvodcem nepodporují všechno, co je potřeba udělat, musíte odkazovat na rozhraní pro tyto třídy v [knihovně šablon OLE DB](../../data/oledb/ole-db-templates.md). Tato rozhraní zabalí nezpracovaná OLE DB rozhraní, která poskytují dodatečnou implementaci, aby je bylo možné snadněji používat.

Například pokud chcete aktualizovat data v sadě řádků, ale zapomněli jste tuto možnost zadat při vytváření příjemce pomocí průvodce, můžete určit funkčnost za faktem nastavením `DBPROP_IRowsetChange` vlastností a `DBPROP_UPDATABILITY` v objektu Command. Poté, když je vytvořena sada řádků, má `IRowsetChange` rozhraní.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Máte starší kód s použitím jiné technologie pro přístup k datům (ADO, ODBC nebo DAO)?

S ohledem na možné kombinace technologií (například používání komponent ADO s komponentami OLE DB a migrace kódu ODBC do OLE DB) se pokrývají všechny situace nad rámec dokumentace k vizuálu C++ . Mnoho článků týkajících se různých scénářů je však k dispozici na následujících webech společnosti Microsoft:

- [Pomoc a podpora společnosti Microsoft](https://support.microsoft.com/)

- [Přehled technických článků o přístupu k datům společnosti Microsoft](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>Viz také:

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)
