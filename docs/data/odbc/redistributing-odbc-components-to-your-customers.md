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
ms.openlocfilehash: 1a6ec6f5fdd3c32080d357ca58d31ccea271b7a4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040083"
---
# <a name="redistributing-odbc-components-to-your-customers"></a>Redistribuce součástí rozhraní ODBC vašim zákazníkům

Pokud funkce programy Správce rozhraní ODBC můžete zahrnout do vaší aplikace, musíte také distribuovat uživatelům soubory, na kterých běží tyto programy. Tyto soubory rozhraní ODBC jsou umístěny v adresáři \OS\System z disku CD-ROM Visual C++. Soubor Redistrb.wri a licenční smlouvy ve stejném adresáři obsahují seznam souborů rozhraní ODBC, které je možné znovu distribuovat.

V dokumentaci pro všechny ovladače rozhraní ODBC, které plánujete k odeslání. Budete muset určit, které knihovny DLL a další soubory k odeslání. Doporučujeme přečíst [Redistribuce součástí rozhraní ODBC vašim zákazníkům](../../data/odbc/redistributing-odbc-components-to-your-customers.md), který vysvětluje, jak Redistribuce součástí rozhraní ODBC.

Kromě toho budete muset zahrnout jeden další soubor ve většině případů. Odbccr32.dll je knihovna kurzorů rozhraní ODBC. Tato knihovna poskytuje schopnost posun vpřed a zpět ovladače úrovně 1. Poskytuje taky možnost podpory snímků. Další informace o knihovna kurzorů rozhraní ODBC naleznete v tématu [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

Další informace o použití rozhraní ODBC s databázovými třídami naleznete v následujících tématech:

- [ODBC: Knihovna kurzorů rozhraní ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md)

- [ODBC: Konfigurace zdroje dat ODBC](../../data/odbc/odbc-configuring-an-odbc-data-source.md)

- [ODBC: Přímé volání funkcí rozhraní API ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)

## <a name="see-also"></a>Viz také:

[ODBC – základy](../../data/odbc/odbc-basics.md)<br/>
[Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md)