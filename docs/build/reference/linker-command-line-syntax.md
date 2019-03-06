---
title: Syntaxe příkazového řádku linkeru
ms.date: 11/04/2016
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
ms.openlocfilehash: 55171c1f16b43e08b5c4a6b078c82f4ed08855d5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422725"
---
# <a name="linker-command-line-syntax"></a>Syntaxe příkazového řádku linkeru

Ke spuštění odkaz. Soubor EXE, použijte tuto syntaxi příkazu:

```
LINK arguments
```

`arguments` Zahrnují možnosti a názvy souborů a dá se zadat v libovolném pořadí. Možnosti jsou zpracované první a soubory. K oddělení argumentů použijte mezery nebo tabulátory.

> [!NOTE]
>  Tento nástroj můžete spustit pouze z příkazového řádku sady Visual Studio. Nelze provést toto spuštění z příkazového řádku systému nebo Průzkumníka souborů.

Na příkazovém řádku možnost sestává ze specifikátoru možnosti, pomlčku (-) nebo lomítkem (/), za nímž následuje název možnosti. Názvy možností nelze zkracovat. Některé možnosti přijímají argument, zadané za dvojtečkou (:). Mezery ani tabulátory jsou povoleny ve specifikaci možnosti, s výjimkou v rámci řetězec v uvozovkách ve variantě pro Comment. Určení argumentů v desítkovém zápisu nebo v zápisu jazyka. Názvy možností a jejich – klíčové slovo nebo název souboru argumenty nejsou velká a malá písmena, ale identifikátory jako argumenty jsou malá a velká písmena.

Do propojovacího programu předat do souboru, zadejte na příkazovém řádku po příkazu LINK název souboru. Můžete zadat absolutní nebo relativní cestu s názvem, a můžete použít zástupné znaky v názvu souboru. Pokud vynecháte tečku (.) a názvem souboru s příponou, odkaz předpokládá .obj za účelem vyhledání souboru. ODKAZ přípony názvu souboru nebo chybějící je, abyste neklikli vytvářet předpoklady o obsah souborů. Určuje typ souboru porovnáním se a zpracovává je odpovídajícím způsobem.

Link.exe vrátí hodnotu 0 pro úspěch (bez chyb).  V opačném případě vrátí linkeru číslo chyby, který zastavil na odkaz.  Například pokud linker vydá LNK1104, linker vrátí 1104.  Nejnižší číslo chyby vrácené v případě chyby linkeru odpovídajícím způsobem, je 1000.  Vrácená hodnota 128 představuje buď problém s operačním systémem nebo o soubor .config. zavaděč se nenačetla link.exe nebo c2.dll.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
