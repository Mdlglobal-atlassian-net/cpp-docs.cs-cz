---
title: Chyba kompilátoru prostředků RC2001
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191717"
---
# <a name="resource-compiler-error-rc2001"></a>Chyba kompilátoru prostředků RC2001

nový řádek v konstantě

Řetězcová konstanta pokračovala na druhém řádku bez zpětného lomítka ( **\\** ) nebo zavření a otevření dvojitých uvozovek ( **"** ).

Chcete-li přerušit řetězcovou konstantu, která je na dvou řádcích ve zdrojovém souboru, proveďte jednu z následujících akcí:

- Ukončí první řádek znakem pokračování řádku, zpětného lomítka.

- Zavřete řetězec na prvním řádku pomocí dvojité uvozovky a otevřete řetězec na dalším řádku s jiným znakem uvozovek.

Není dostačující pro ukončení prvního řádku s \n, řídicí sekvence pro vložení znaku nového řádku v řetězcové konstantě.
