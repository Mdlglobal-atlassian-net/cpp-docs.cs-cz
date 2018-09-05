---
title: Pomocí šablony knihovny (ATL) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- template libraries
ms.assetid: 5e80ec6e-a61c-41ce-b34b-9a6252c46265
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91a9c10bef285780ded145e33800ebd3db198827
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754783"
---
# <a name="using-a-template-library"></a>Použití knihovny šablon

Šablona je něco jako makra. Stejně jako u makra, volání šablony způsobí, že umožňuje rozbalit (s odpovídající parametr nahrazení) na kód, který jste napsali. Nicméně šablony širší než povolíte vytváření nových tříd na základě typů, které se předávají jako parametry. Tyto nové třídy implementaci zajišťující bezpečnost typů způsoby provedení operace vyjádřit v kódu šablony.

Knihovny šablon, jako je například ATL nejsou ze své podstaty nebo nemusí být hierarchicky a se liší od tradiční knihovny tříd jazyka C++, jsou obvykle dodávány pouze jako zdrojový kód (nebo jako zdrojový kód s malým, podpora doby běhu). Místo odvozování z třídy za účelem získání funkce, které očekáváte, můžete vytvořit instanci třídy ze šablony.

## <a name="see-also"></a>Viz také

[Úvod do ATL](../atl/introduction-to-atl.md)

