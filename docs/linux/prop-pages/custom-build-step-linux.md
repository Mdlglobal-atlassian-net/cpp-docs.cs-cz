---
title: Custom Build Step Properties (Linux C++)
ms.date: 10/17/2017
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 5e6580263e63547e3564eaee260158a312e5fa6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393113"
---
# <a name="custom-build-step-properties-linux-c"></a>Custom Build Step Properties (Linux C++)

Vlastnost | Popis
--- | ---
Příkazový řádek | Příkaz, který má vlastní krok sestavení provést.
Popis | Zpráva, která se zobrazí při spuštění vlastního kroku sestavení
Výstupy | Výstupní soubor, který je vygenerován vlastním krokem sestavení. Toto nastavení je povinné, aby přírůstkové sestavení fungovalo správně.
Další závislosti | Seznam případných dalších vstupních souborů, které se mají použít ve vlastním kroku sestavení, oddělených středníkem.
Po spuštění a provést před | Tyto volby definují, kdy se vlastní krok v rámci procesu sestavení spustí. Zadávají se ve vztahu k cílům uvedeným v seznamu. Nejčastěji používané cíle jsou BuildGenerateSources, BuildCompile a BuildLink, které představují nejdůležitější kroky v procesu sestavení. Další často používané cíle jsou Midl, CLCompile a Link.
Považovat výstup za obsah | Tato možnost je pouze smysl pro Microsoft Store nebo Windows Phone aplikací, které v balíčku .appx zahrnují všechny obsahové soubory.