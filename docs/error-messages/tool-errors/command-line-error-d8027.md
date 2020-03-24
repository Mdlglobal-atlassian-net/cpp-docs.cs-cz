---
title: Chyba příkazového řádku D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 42341507dfc2d3da02639dd28ab1265783452388
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196882"
---
# <a name="command-line-error-d8027"></a>Chyba příkazového řádku D8027

nejde spustit součást.

Kompilátor nemůže spustit danou komponentu kompilátoru nebo linker.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Pro načtení součásti není dostatek paměti. Pokud modul NMAKE vyvolal kompilátor, spusťte kompilátor mimo soubor pravidel.

1. Aktuální operační systém nemohl spustit součást. Ujistěte se, že cesta odkazuje na spustitelné soubory, které jsou vhodné pro váš operační systém.

1. Součást byla poškozena. Zkopírujte komponentu z distribučních disků pomocí INSTALAČNÍho programu.

1. Možnost byla nesprávně zadána. Příklad:

    ```
    cl /B1 file1.c
    ```
