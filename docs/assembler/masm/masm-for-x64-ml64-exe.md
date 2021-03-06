---
title: MASM pro x64 (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 5e324414a0d4d7e74bb28d54c1d858ef6fb9793c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312739"
---
# <a name="masm-for-x64-ml64exe"></a>MASM pro x64 (ml64.exe)

Visual Studio zahrnuje 32 a 64 bitové hostované verze Microsoft assembleru (MASM) do cíle kódu x64. S názvem ml64. exe se jedná o Assembler, který přijímá jazyk x64 Assembler. Nástroje příkazového řádku MASM se instalují při výběru zatížení během instalace C++ sady Visual Studio. Nástroje MASM nejsou k dispozici jako samostatné stažení. Pokyny ke stažení a instalaci kopie sady Visual Studio naleznete v tématu [install Visual Studio](/visualstudio/install/install-visual-studio). Pokud nechcete instalovat celé rozhraní IDE sady Visual Studio, ale chcete pouze nástroje příkazového řádku, Stáhněte si [Nástroje sestavení pro Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019).

Chcete-li použít MASM k sestavení kódu pro cíle x64 na příkazovém řádku, je nutné použít příkazový řádek pro vývojáře pro cíle x64, který nastaví požadovanou cestu a další proměnné prostředí. Informace o spuštění příkazového řádku pro vývojáře naleznete v tématu [sestavení C/C++ Code v příkazovém řádku](../../build/building-on-the-command-line.md).

Informace o možnostech příkazového řádku ml64. exe najdete v tématu Referenční dokumentace k [příkazovému řádku ml a ML64](ml-and-ml64-command-line-reference.md).

Inline assembler nebo použití klíčového slova ASM není podporováno pro cíle x64 a ARM. Chcete-li svůj kód x86 použít pro inline assembleru na x64 nebo ARM, můžete převést kód C++na, použít vnitřní objekty kompilátoru nebo vytvořit zdrojové soubory assembleru jazyka assembleru. Kompilátor společnosti C++ Microsoft podporuje vnitřní funkce, díky kterým můžete v případě potřeby použít pokyny speciální funkce, například privilegované, bitovou kontrolu/testování, prolínání a tak dále, a to co nejblíže k platformě pro různé platformy. Informace o dostupných vnitřních objektech naleznete v tématu [vnitřní objekty kompilátoru](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Přidání souboru jazyka assembleru do projektu sady Visual Studio C++

Systém projektu sady Visual Studio podporuje soubory Assembler-Language sestavené pomocí MASM ve vašich C++ projektech. Můžete vytvářet zdrojové soubory jazyka x64 assembleru a sestavovat je do souborů objektů pomocí MASM, který podporuje plně x64. Pak můžete propojit tyto soubory objektů s vaším C++ kódem vytvořeným pro cíle x64. Toto je jeden ze způsobů, jak překonat chybějící rozhraní inline assembleru x64.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Přidání souboru jazyka assembleru do existujícího projektu sady Visual Studio C++

1. Vyberte projekt v **Průzkumníka řešení**. Na panelu nabídek vyberte možnost **projekt**, **přizpůsobení sestavení**.

1. V dialogovém **okně C++ Visual Build Customization Files** zaškrtněte políčko vedle **MASM (. targets,. props)** . Kliknutím na **tlačítko OK** uložte výběr a zavřete dialogové okno.

1. Na panelu nabídek vyberte možnost **projekt**, **Přidat novou položku**.

1. V dialogovém okně **Přidat novou položku** vyberte  **C++ v prostředním podokně soubor (. cpp)** . V ovládacím prvku upravit **název** zadejte nový název souboru, který má příponu **. asm** místo. cpp. Zvolením možnosti **Přidat** přidejte soubor do projektu a zavřete dialogové okno.

Vytvořte kód assembleru-Language v souboru. ASM, který jste přidali. Při sestavování řešení je vyvolána MASM Assembler pro sestavení souboru. asm do souboru objektu, který je poté propojen do projektu. Chcete-li usnadnit přístup k symbolům, deklarujte své funkce assembleru jako `extern "C"` ve C++ zdrojovém kódu C++ namísto použití konvence dekorace názvů ve zdrojových souborech assembleru jazyka.

## <a name="ml64-specific-directives"></a>Direktivy specifické pro ml64

Ve zdrojovém kódu vašeho jazyka assembleru, který cílí na x64, můžete použít následující direktivy ml64:

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

Direktiva [proc](proc.md) se navíc aktualizovala pro použití s ml64. exe.

## <a name="32-bit-address-mode-address-size-override"></a>32 – režim bitové adresy (přepsání velikosti adresy)

MASM vygeneruje přepsání velikosti 0x67 adres, pokud operand paměti obsahuje 32 bitů. Například následující příklady způsobí, že bude vygenerováno přepsání velikosti adresy:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM předpokládá, že pokud se navýšení 32 bitového posunu zobrazuje samostatně jako operand paměti, je určeno 64 adresování. V současnosti není podporována podpora 32 bitového adresování s takovými operandy.

Nakonec vymíchat velikosti registrů v rámci operandu paměti, jak je znázorněno v následujícím kódu, vygeneruje chybu.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](microsoft-macro-assembler-reference.md)
