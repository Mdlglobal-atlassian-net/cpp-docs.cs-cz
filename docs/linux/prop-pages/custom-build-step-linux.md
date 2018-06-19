---
title: Vlastní sestavovací krok vlastnosti (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 0ec787826a09379732ac00fa858d32f05cf8025b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326069"
---
# <a name="custom-build-step-properties-linux-c"></a>Vlastní sestavovací krok vlastnosti (Linux C++)

Vlastnost | Popis
--- | ---
Příkazový řádek | Příkaz, který má vlastní krok sestavení provést.
Popis | Zpráva, která se zobrazí při spuštění vlastního kroku sestavení
Výstupy | Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně.
Další závislosti | Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem.
Po spuštění a provést před | Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link.
Považovat výstup za obsah | Tato možnost je jenom pro aplikace Microsoft Store nebo Windows Phone, které zahrnují všechny soubory obsahu v balíčku .appx smysluplný.