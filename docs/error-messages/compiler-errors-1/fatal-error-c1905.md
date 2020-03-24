---
title: Závažná chyba C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 106dfe8a078047225097686d185a1ba43987ce33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202621"
---
# <a name="fatal-error-c1905"></a>Závažná chyba C1905

Strana klientu a strana serveru nejsou kompatibilní (musí cílit na stejný procesor)

K této chybě dochází, když je soubor. obj vygenerovaný front-end kompilátorem (C1. dll), který cílí na jeden procesor, jako je například x86, ARM nebo x64, ale čte ho back-end (C2. dll), který cílí na jiný procesor.

Chcete-li tento problém vyřešit, ujistěte se, že používáte odpovídající front-end a back-end. Toto je výchozí nastavení pro projekty vytvořené v aplikaci Visual Studio. K této chybě může dojít, pokud jste upravili soubor projektu a použili jste jiné cesty k nástrojům kompilátoru. Pokud jste nastavili specifickou cestu pro nástroje kompilátoru, pak k této chybě může dojít, pokud je instalace sady Visual Studio poškozená. Mohli jste například zkopírovat soubory Compiler. dll z jednoho umístění do jiného. Pomocí **programů a funkcí** v Ovládacích panelech systému Windows opravte nebo přeinstalujte sadu Visual Studio.
