---
title: Redistribuce součástí rozhraní ODBC vašim zákazníkům
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC components, redistributing
- ODBC, distributing components
- components [C++], distributing
- ODBC Administrator
- components [C++]
- components [C++], redistributing
ms.assetid: 17b065b4-a307-4b89-99ac-d05831cfab87
ms.openlocfilehash: 0d4d3948add665c54be3d3b0596a7a6fc0e414f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212729"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuce součástí rozhraní ODBC vašim zákazníkům

Pokud zachováte funkce programů správce rozhraní ODBC do vaší aplikace, musíte také distribuovat uživatelům soubory, které tyto programy spouštějí. Tyto soubory ODBC jsou umístěné v adresáři \OS\System Visual C++ CD-ROM. Soubor Redistrb. wri a licenční smlouva ve stejném adresáři obsahují seznam souborů ODBC, které můžete znovu distribuovat.

Projděte si dokumentaci pro všechny ovladače rozhraní ODBC, které plánujete odeslat. Musíte určit, které knihovny DLL a jiné soubory budou dodávány. Měli byste si také přečíst [komponenty rozhraní ODBC pro vaše zákazníky](../../data/odbc/redistributing-odbc-components-to-your-customers.md), což vysvětluje, jak distribuovat komponenty rozhraní ODBC.

Kromě toho musíte do většiny případů zahrnout jeden další soubor. ODBCCR32. dll je knihovna kurzorů rozhraní ODBC. Tato knihovna poskytuje ovladačům úrovně 1 možnosti dopředu a zpětně posunutí. Poskytuje také schopnost podporovat snímky. Další informace o knihovně kurzorů rozhraní ODBC naleznete v tématu [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

V následujících tématech najdete další informace o používání rozhraní ODBC s databázovými třídami:

- [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Konfigurace zdroje dat ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Přímé volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Viz také

[ODBC – základy](../../data/odbc/odbc-basics.md)<br/>
[Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)
