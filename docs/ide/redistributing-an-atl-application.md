---
title: Redistribuování aplikace ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6db7e553d2f9e268b39bb9c02e70bb59815aef3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405930"
---
# <a name="redistributing-an-atl-application"></a>Redistribuování aplikace ATL

Spouští se v sadě Visual Studio 2012, je aktivní šablony knihovny (ATL) knihovny jen pro záhlaví. Projekty knihovny ATL DLL knihovny ATL, možnosti nemají. Žádné redistribuovatelné knihovny ATL je povinný.

Pokud redistribuujete spustitelná aplikace ATL, budete muset zaregistrovat soubor .exe (a všechny ovládací prvky uvnitř) pomocí následujícího příkazu:

```
filename /regserver
```

kde `filename` je název spustitelného souboru.

V sadě Visual Studio 2010 se sestaví projekt knihovny ATL pro MinDependency nebo Konfigurace MinSize. Konfigurace MinDependency je, co všechno získáte při nastavení **použití knihovny ATL** vlastnost **statické propojení s knihovnou ATL** na **Obecné** stránku vlastností a nastavte  **Knihovna prostředí runtime** vlastnost **Vícevláknová (/ MT)** na **generování kódu** stránka vlastností (složka C/C++).

MinSize konfigurace je, co všechno získáte při nastavení **použití knihovny ATL** vlastnost **dynamické propojení s knihovnou ATL** na **Obecné** stránku vlastností nebo nastavte **modulu Runtime Knihovna** vlastnost **Multi-threaded DLL (/ MD)** na **generování kódu** stránka vlastností (složka C/C++).

MinSize vytvoří výstupní soubor malý, jak je možné, ale vyžaduje, aby knihovny ATL100.dll a Msvcr100.dll (Pokud jste vybrali **Multi-threaded DLL (/ MD)** možnost) jsou na cílovém počítači. Knihovna ATL100.dll by měl být zaregistrován v cílovém počítači, který zajišťuje všechny funkce ATL k dispozici. Knihovna ATL100.dll obsahuje ANSI a Unicode exporty.

Pokud vytvoříte projekt knihovny ATL nebo šablony technologie OLE DB pro cíl MinDependency, nepotřebujete k instalaci a registraci Knihovna ATL100.dll v cílovém počítači, ale může se zobrazit větší obrázek programu.

Pokud redistribuujete spustitelná aplikace ATL, budete muset zaregistrovat soubor .exe (a všechny ovládací prvky uvnitř) pomocí následujícího příkazu:

```
filename /regserver
```

kde `filename` je název spustitelného souboru.

## <a name="see-also"></a>Viz také

[Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)