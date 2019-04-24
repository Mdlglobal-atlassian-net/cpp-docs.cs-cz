---
title: ATL Services
ms.date: 11/04/2016
helpviewer_keywords:
- CServiceModule class
- COM objects, ATL
- services, ATL
- ATL services
ms.assetid: 8c09d1a8-7548-4d2c-947c-9d795a81659b
ms.openlocfilehash: 052169154a62cbd07a82f08087fc2c2db8ae46c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62251912"
---
# <a name="atl-services"></a>ATL Services

Chcete-li vytvořit objekt knihovny ATL modelu COM, tak, aby běžel ve službě, stačí vyberte služby (EXE) ze seznamu možností serveru v Průvodci vytvořením projektu ATL. Průvodce potom vytvoří třídu odvozenou z `CAtlServiceModuleT` pro implementaci této služby.

Při vytváření objektu knihovny ATL modelu COM jako služba, se zaregistruje pouze jako místní server, a nebude se zobrazovat v seznamu služeb v Ovládacích panelech. Toto je vzhledem k tomu je snazší ladění služby jako místní server než jako služba. Ho Pokud chcete nainstalovat jako službu, spusťte na příkazovém řádku následující:

`YourEXE``.exe /Service`

Chcete-li ho odinstalovat, spusťte následující příkaz:

`YourEXE``.exe /UnregServer`

První čtyři témata v této části popisují akce, které nastanou během provádění `CAtlServiceModuleT` členské funkce. Tato témata se zobrazí ve stejném pořadí jako funkce se běžně označují jako. Pokud chcete zlepšit pochopíte z těchto témat, je vhodné použít zdrojový kód vygenerovaný Průvodce projektem ATL jako odkaz. Tato první čtyři témata jsou:

- [Catlservicemodulet::Start – funkce](../atl/reference/catlservicemodulet-class.md#start)

- [Catlservicemodulet::servicemain – funkce](../atl/reference/catlservicemodulet-class.md#servicemain)

- [Catlservicemodulet::Run – funkce](../atl/reference/catlservicemodulet-class.md#run)

- [Catlservicemodulet::Handler – funkce](../atl/reference/catlservicemodulet-class.md#handler)

Poslední tři témata se zabývají koncepty související s vývojem služby:

- [Položky registru](../atl/registry-entries.md) služby ATL

- [DCOMCNFG](../atl/dcomcnfg.md)

- [Tipy pro ladění](../atl/debugging-tips.md) služby ATL

## <a name="see-also"></a>Viz také:

[Koncepty](../atl/active-template-library-atl-concepts.md)
