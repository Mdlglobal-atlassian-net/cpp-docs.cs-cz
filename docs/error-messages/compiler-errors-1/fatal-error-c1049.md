---
title: Závažná chyba C1049
description: Popisuje závažnou chybu kompilátoru C1049, neplatný číselný argument a vysvětluje, jak ho vyřešit.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: f2669eec4bafb24f26c405d4fa74a96fe5337d13
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633194"
---
# <a name="fatal-error-c1049"></a>Závažná chyba C1049

> Neplatný číselný argument*Value*

CL. Analyzátor příkazového řádku EXE nalezl *hodnotu* , kde byla očekáván číselný argument.

Pokud kompilátor nemůže najít číselný argument pro jednu z těchto možností kompilátoru, může dojít k chybě C1049:

[/constexpr: hloubka](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr:\ zpětného trasování](/cpp/build/reference/constexpr-control-constexpr-evaluation)
[/constexpr: kroky](/cpp/build/reference/constexpr-control-constexpr-evaluation)

Možnosti kompilátoru příkazového řádku, které očekávají číselný argument, mohou také nahlásit `Command line error D8004`, `Command line error D8021`, `Command line warning D9002`, `Command line warning D9014`nebo `Command line warning D9024`.

Chcete-li tuto chybu vyřešit, Projděte si příkazový řádek pro chybné umístění nebo chybějící argumenty. Ověřte, že mezi parametry a argumenty není žádný neočekávaný prázdný znak. Poslední příkazový řádek může být vygenerován makry, proměnnými prostředí nebo jinými operacemi systému sestavení. To je důvod, proč je důležité se podívat na skutečný příkazový řádek předaný kompilátoru.

- V souborech příkazů nebo souborů pravidel můžete použít příkaz **echo** k nahlášení aktuálního příkazového řádku.

- V aplikaci Visual Studio otevřete dialogové okno **stránky vlastností** projektu. Na stránce **Vlastnosti konfigurace** > **Obecná** stránka **C++ C/**  > změňte vlastnost **Potlačit úvodní nápis** na hodnotu **ne**. Kliknutím na **tlačítko OK** uložte změny. Okno **výstup** nyní zobrazuje příkazový řádek při sestavování, hned za linku copyrightu.

Další systémy sestavení mohou mít soubory protokolu nebo podrobné možnosti, aby bylo možné zobrazit samotné použité příkazy. Informace najdete v dokumentaci k systému sestavení.
