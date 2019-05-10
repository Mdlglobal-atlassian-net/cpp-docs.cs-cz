---
title: MASM pro x64 (ml64.exe)
ms.date: 08/30/2018
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 1a92d2a22e8aa9df29c18fa36ff4508eb8eec57f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65445862"
---
# <a name="masm-for-x64-ml64exe"></a>MASM pro x64 (ml64.exe)

Visual Studio obsahuje 32bitové a 64bitové prostředí verze Microsoft Assembler (MASM) na cílový x64 kód. S názvem ml64.exe, toto je assembler, který přijímá x64 jazyka assembleru. Nástroje příkazového řádku MASM nainstalují při výběru úlohy pro C++ během instalace sady Visual Studio. MASM nástroje nejsou k dispozici jako samostatný soubor ke stažení. Pokyny o tom, jak stáhnout a nainstalovat jeho kopii sady Visual Studio najdete v tématu [instalace sady Visual Studio](/visualstudio/install/install-visual-studio). Pokud chcete nainstalovat úplné rozhraní IDE sady Visual Studio, ale zajímá jenom nástroje příkazového řádku, stáhněte si [Build Tools pro Visual Studio](https://visualstudio.microsoft.com/downloads/).

Použití MASM k vytváření kódu pro x64, zaměřuje na příkazovém řádku, je nutné použít příkazový řádek vývojáře pro x64 cíle, které nastaví tato cesta i ostatním proměnným prostředí. Informace o tom, jak spustit příkazový řádek pro vývojáře najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md).

Informace o možnostech příkazového řádku ml64.exe najdete v tématu [ML a ml64 v příkazovém Reference k příkazovému řádku](../../assembler/masm/ml-and-ml64-command-line-reference.md).

Vložený assembler nebo použití klíčového slova ASM se nepodporuje pro x64 nebo cíle ARM. K portu vašeho x86 kódu tohoto použití inline assembleru x64 nebo ARM, můžete převést kódu jazyka c++, použít vnitřní funkce kompilátoru nebo vytvořit zdrojové soubory jazyka assembleru. Microsoft C++ kompilátor podporuje vnitřních objektů, aby bylo možné použít speciální funkce pokyny pro příklad privilegovaného, bit kontrolu a testování, interlocked a tak dále, v jako blízko způsobem napříč platformami jako je to možné. Informace o vnitřní objekty dostupné, najdete v části [vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md).

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>Přidání souboru jazyka assembleru do sady Visual Studio C++ projektu

Systém projektu sady Visual Studio podporuje assembleru jazyka soubory sestavené s využitím MASM ve svých projektech C++. Můžete vytvořit x64 assembleru jazyka zdrojové soubory a sestavení je do souborů objektů pomocí MASM, která plně podporuje x64. Pak můžete propojit tyto soubory objekt kódu jazyka C++ vytvořené pro x64 cíle. Toto je jeden způsob, jak překonat chybějící x x64 inline assembleru.

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>Přidání souboru jazyka assembleru do existující sady Visual Studio C++ projektu

1. Vyberte projekt v **Průzkumníka řešení**. V panelu nabídky zvolte **projektu**, **přizpůsobení sestavení**.

1. V **Visual C++ soubory úpravy sestavení** dialogové okno pole, zaškrtněte políčko vedle **masm(.targets,.props)**. Zvolte **OK** výběr uložte a zavřete dialogové okno.

1. V panelu nabídky zvolte **projektu**, **přidat novou položku**.

1. V **přidat novou položku** dialogu **soubor C++ (.cpp)** v prostředním podokně. V **název** ovládacích prvků pro úpravy, zadejte nový název souboru, který má **.asm** rozšíření místo .cpp. Zvolte **přidat** přidejte soubor do projektu a zavřete dialogové okno.

Vytvoření kódu assembleru jazyka do souboru .asm, kterou jste přidali. Při sestavení vašeho řešení, je vyvolána MASM assembler do souboru .asm sestavení do souboru objektu, který se pak propojí do vašeho projektu. Pro usnadnění přístupu symbol deklarace vašich funkcí assembler jako `extern "C"` ve zdrojovém kódu C++, místo použití jazyka C++ název dekorace konvencí ve vašem jazyce assembler zdrojové soubory.

## <a name="ml64-specific-directives"></a>Direktivy pro konkrétní ml64 v příkazovém

Můžete použít následující direktivy pro konkrétní ml64 v příkazovém ve zdrojovém kódu assembleru jazyka, který se zaměřuje x64:

- [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)

- [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)

- [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)

- [.PUSHREG](../../assembler/masm/dot-pushreg.md)

- [.SAVEREG](../../assembler/masm/dot-savereg.md)

- [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)

- [.SETFRAME](../../assembler/masm/dot-setframe.md)

Kromě toho [PROC](../../assembler/masm/proc.md) – direktiva byl aktualizován pro použití s ml64.exe.

## <a name="32-bit-address-mode-address-size-override"></a>Režim adresy 32-bit (adresa velikost přepsání)

MASM vysílá přepsání velikost adresy 0x67 Pokud operand paměti zahrnuje 32-bit registrů. Například následující příklady způsobit přepsání velikost adresy emitování:

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM předpokládá, že pokud se zobrazí pouze jako operand paměti posunu 32-bit, 64-bit adresování je určena. Aktuálně není dostupná podpora pro 32-bit adresování pomocí těchto operandů.

A konečně kombinování velikosti registru v rámci paměti operand, jak je ukázáno v následujícím kódu, dojde k chybě.

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>