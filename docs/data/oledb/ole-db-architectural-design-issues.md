---
title: Problémy s návrhem technologie OLE DB
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: 2f0a7a114c671e17d8f95280ab00ed93570e8609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395557"
---
# <a name="ole-db-architectural-design-issues"></a>Problémy s návrhem technologie OLE DB

Před zahájením aplikaci OLE DB, zvažte následující otázky:

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>Jaké programovací implementace použijete k zápisu aplikaci OLE DB?

Společnost Microsoft nabízí několik knihoven k provedení této úlohy: knihovny šablon technologie OLE DB, atributy technologie OLE DB a raw rozhraní OLE DB v SDK technologie OLE DB. K dispozici je také průvodců, snadněji napsat program. Tato implementace jsou popsány v [šablony technologie OLE DB, atributy a jiné implementace](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).

## <a name="do-you-need-to-write-your-own-provider"></a>Je třeba napsat vlastního zprostředkovatele?

Většina vývojářů není potřeba psát vlastní poskytovatele. Společnost Microsoft poskytuje několik poskytovatelů. Při vytváření datového připojení (například když přidáte příjemce do vašeho projektu pomocí **průvodce příjemcem ATL OLE DB**), **vlastnosti propojení dat** dialogové okno zobrazí seznam všech dostupných zprostředkovatelů registrované ve vašem systému. Pokud jednoho z těchto poskytovatelů je vhodný pro vlastní datové úložiště a data aplikace přístup, je nejjednodušší krokem je použít jednu z následujících. Nicméně pokud vaše úložiště dat neodpovídá velikosti jedné z těchto kategorií, budete muset vytvořit vlastního zprostředkovatele. Informace o vytváření poskytovatelů najdete v tématu [šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>Jaké úroveň podpory je potřeba pro vaše?

Některé příjemce může být basic. zatímco jiné můžou být složité. Funkce pro objekty OLE DB je zadána vlastností. Při použití **průvodce příjemcem ATL OLE DB** vytvořte příjemce nebo **Průvodce zprostředkovatelem databáze** k vytvoření poskytovatele, nastaví odpovídající objekt vlastnosti vám umožní poskytovat standardní sadu funkce. Ale pokud příjemce nebo zprostředkovatele třídy generované v Průvodci nepodporují všechno, co budete potřebovat udělat, musíte odkazovat na rozhraní pro tyto třídy v [knihovny šablon technologie OLE DB](../../data/oledb/ole-db-templates.md). Tato rozhraní zabalit nezpracovaná rozhraní technologie OLE DB poskytují dodatečné implementace pro usnadnění jejich používání za vás.

Například pokud chcete aktualizovat data v sadě řádků, ale zapomněli zadat při vytváření příjemce pomocí průvodce, můžete zadat funkce po jejich výskytu tak, že nastavíte `DBPROP_IRowsetChange` a `DBPROP_UPDATABILITY` vlastnosti v objektu command. Poté, když se v sadě řádků, má `IRowsetChange` rozhraní.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>Máte starší kód pomocí jiné technologie přístup data (ADO, ODBC a DAO)?

Je to možné kombinace technologií (jako jsou komponenty technologie OLE DB pomocí komponenty ADO a migrace kód rozhraní ODBC do technologie OLE DB), zahrnující všechny situace je nad rámec dokumentace k Visual C++. Řada článků pokrývajících různé scénáře jsou však k dispozici na na následujících webech Microsoftu:

- [Nápovědu a podporu Microsoftu](https://support.microsoft.com/)

- [Přehled technické články k přístupu k datům společnosti Microsoft](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>Viz také:

[Programování v architektuře OLE DB](../../data/oledb/ole-db-programming.md)<br/>
[Přehled programování v architektuře OLE DB](../../data/oledb/ole-db-programming-overview.md)
