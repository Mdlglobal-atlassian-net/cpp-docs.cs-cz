---
title: /Zm (Zadat omezení přidělení paměti pro předkompilované hlavičky)
ms.date: 11/04/2016
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: ee42fc2d1065a755fa816a99563ccc9f0108e847
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634795"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Zadat omezení přidělení paměti pro předkompilované hlavičky)

Určuje množství paměti, které kompilátor přiděluje k vytvoření předkompilovaných hlaviček.

## <a name="syntax"></a>Syntaxe

```
/Zmfactor
```

## <a name="arguments"></a>Arguments

*faktor*<br/>
Škálovací faktor určující množství paměti, které kompilátor používá k vytvoření předkompilovaných hlaviček.

*Faktor* argument je procento výchozí velikosti vyrovnávací paměti definované kompilátorem práce. Výchozí hodnota *faktor* je 100 (procent), můžete ale zadat větší nebo menší hodnoty.

## <a name="remarks"></a>Poznámky

Ve starších verzích jazyka Visual C++ používal kompilátor několik samostatných hald, přičemž každá měla konečný limit. V současné době kompilátor haldu dynamicky zvětšuje podle potřeby až do celkového limitu velikosti a vyrovnávací paměť fixní velikosti vyžaduje pouze k vytvoření předkompilovaných hlaviček. V důsledku toho **/Zm** – možnost kompilátoru je zřídka nezbytné.

Pokud kompilátoru dojde prostor haldy a generuje [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) chybová zpráva při použití **/Zm** – možnost kompilátoru, zřejmě jste vyhradili příliš mnoho paměti. Zvažte možnost Odebrat **/Zm** možnost. Pokud kompilátor vydá [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) chybová zpráva, je v doprovodné [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) ve zprávě je obsažený *faktor* argument má použít při opětovné kompilaci pomocí **/Zm** – možnost kompilátoru.

Následující tabulka ukazuje jak *faktor* argument ovlivňuje limit přidělení paměti. Pokud budete předpokládat, že velikost výchozí vyrovnávací paměti předkompilovaných hlaviček je 75 MB.

|Hodnota *faktor*|Limit přidělení paměti|
|-----------------------|-----------------------------|
|10|7.5 MB|
|100|75 MB|
|200|150 MB|
|1000|750 MB|
|2000|1 500 MB|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Jiné způsoby nastavení limitu přidělení paměti

#### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení parametru kompilátoru /Zm ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. V navigačním podokně vyberte **vlastnosti konfigurace**, **C/C++**, **příkazového řádku**.

1. Zadejte **/Zm** – možnost kompilátoru v **další možnosti** pole.

#### <a name="to-set-the-zm-compiler-option-programmatically"></a>Programové nastavení parametru kompilátoru /Zm

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)