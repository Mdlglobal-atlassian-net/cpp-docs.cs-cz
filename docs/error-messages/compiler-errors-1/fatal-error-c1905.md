---
title: Závažná chyba C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 3fb4db30d91e0dd8c9dbeeebca46210122e5ff07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166812"
---
# <a name="fatal-error-c1905"></a>Závažná chyba C1905

Strana klientu a strana serveru nejsou kompatibilní (musí cílit na stejný procesor)

Tato chyba nastane, pokud soubor .obj generován kompilátoru front-endu (C1.dll) tohoto cíle jeden procesor, jako je například x86 ARM nebo x64, ale je čten stranou serveru back-end (C2.dll), který se zaměřuje na jiný procesor.

Chcete-li vyřešit tento problém, ujistěte se, že používáte odpovídající front-endu a back-endu. Toto je výchozí nastavení pro projekty vytvořené v sadě Visual Studio. K této chybě může dojít, pokud jste upravili soubor projektu a použít různé cesty k nástrojům kompilátoru. Pokud jste nenastavili konkrétně cestu k nástrojům kompilátoru, této chybě může dojít v případě, že instalaci sady Visual Studio je poškozený. Například pravděpodobně jste zkopírovali soubory DLL kompilátoru z jednoho umístění do druhého. Použití **programy a funkce** v Ovládacích panelech Windows opravte nebo přeinstalujte Visual Studio.