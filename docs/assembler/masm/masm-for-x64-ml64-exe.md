---
title: MASM pro x64 (ml64.exe) | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2018
ms.technology:
- cpp-masm
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb4f4a0ba996be34749350c0d99c1915752fe99e
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322245"
---
# <a name="masm-for-x64-ml64exe"></a>MASM pro x64 (ml64.exe)

Visual Studio obsahuje 32bitové a 64bitové verze hostované verze assembleru Microsoft (MASM) do cílové x64 kódu. S názvem ml64.exe, to je assembleru, který přijímá x64 assembleru jazyk. Nástroje příkazového řádku MASM se instalují, když zvolíte C++ zatížení při instalaci sady Visual Studio. Nástroje pro MASM nejsou k dispozici jako samostatný soubor ke stažení. Pokyny o tom, jak stáhnout a nainstalovat kopii sady Visual Studio najdete v tématu [instalaci sady Visual Studio](/visualstudio/install/install-visual-studio). Pokud jste neinstalujte dokončení Visual Studio IDE, ale chcete jenom nástroje příkazového řádku, stáhněte si [nástroje sestavení pro Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

Použít vytvářet MASM kód pro x64 cílí na příkazovém řádku, musíte použít příkazový řádek vývojáře pro x64 cíle, které nastaví požadované cesty a jiných proměnných prostředí. Informace o tom, jak spustit příkazový řádek vývojáře najdete v tématu [kódu sestavení C/C++ v příkazovém řádku](../../build/building-on-the-command-line.md).

Informace o možnostech příkaz ml64.exe najdete v tématu [ML a ml64 v příkazovém Reference k příkazovému řádku](../../assembler/masm/ml-and-ml64-command-line-reference.md).  
  
Vložený assembler nebo použití klíčového slova ASM není podporována pro x64 nebo ARM cíle. K portu vaší x86 kódu vloženého assembleru této používá k x64 nebo ARM, můžete převést kódu C++, použít vnitřní funkce kompilátoru nebo vytvořit assembleru jazyk zdrojové soubory. Visual C++ compiler podporuje – vnitřní prvky umožňují používat funkce zvláštní pokyny pro příklad, privilegovaný, bit kontroly a testovací interlocked a tak dále, v jako blízko napříč platformami způsobem nejblíže. Informace o dostupných vnitřní funkce, najdete v části [vnitřní funkce kompilátoru](../../intrinsics/compiler-intrinsics.md).  

## <a name="add-an-assembler-language-file-to-a-visual-c-project"></a>Přidání souboru assembleru jazyk do projektu Visual C++  
  
Systém projektu sady Visual Studio podporuje assembleru jazykové soubory, které jsou vytvořené pomocí MASM ve vašich projektů C++. Můžete vytvořit x64 assembleru jazyk zdrojové soubory a sestavení je do objektu souborů pomocí MASM, která plně podporuje x64. Pak můžete propojit tyto soubory objekt kódu C++ vytvořené pro x64 cíle. Toto je jedním ze způsobů k překonání nedostatečná x64 vloženého assembleru.  

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-c-project"></a>Chcete-li přidat soubor assembleru jazyk do existujícího projektu Visual C++

1. Vyberte projekt v **Průzkumníku řešení**. Na řádku nabídek zvolte **projektu**, **sestavení přizpůsobení**.

1. V **souborů Visual C++ sestavení přizpůsobení** dialogové okno pole, zaškrtněte políčko vedle **masm(.targets,.props)**. Zvolte **OK** výběr uložte a zavřete dialogové okno.

1. Na řádku nabídek zvolte **projektu**, **přidat novou položku**. 

1. V **přidat novou položku** dialogové okno, vyberte **soubor C++ ()** v prostředním podokně. V **název** ovládacích prvků pro úpravy, zadejte nový název souboru, který má **.asm** rozšíření místo sada. Zvolte **přidat** soubor přidat do projektu a zavřete dialogové okno.

Vytvořte assembleru jazyk kódu v souboru .asm, které jste přidali. Při sestavování řešení, je vyvolána assembleru MASM ke kompilaci souboru .asm do souboru objektu, který je pak propojí do projektu. Pro usnadnění přístupu symbol deklarovat assembleru funkcí jako `extern "C"` ve zdrojovém kódu C++, místo použití C++ název dekorování názvů v jazyka assembleru zdrojové soubory.
  
## <a name="ml64-specific-directives"></a>Specifické pro ml64 v příkazovém direktivy  

Můžete použít následující direktivy ml64 v příkazovém konkrétní ve zdrojovém kódu jazyka assembleru zacílený x64:  
  
-   [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md)  
  
-   [.ENDPROLOG](../../assembler/masm/dot-endprolog.md)  
  
-   [.PUSHFRAME](../../assembler/masm/dot-pushframe.md)  
  
-   [.PUSHREG](../../assembler/masm/dot-pushreg.md)  
  
-   [.SAVEREG](../../assembler/masm/dot-savereg.md)  
  
-   [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md)  
  
-   [.SETFRAME](../../assembler/masm/dot-setframe.md)  
  
Kromě toho [PROC](../../assembler/masm/proc.md) – direktiva byla aktualizována pro použití s ml64.exe.  
  
## <a name="32-bit-address-mode-address-size-override"></a>32-bit adresu režimu (přepsání velikost adres)  

MASM vysílá přepsání velikost 0x67 adresu, pokud operand paměti zahrnuje registry 32-bit. Například následující příklady způsobit přepsání velikost adresy pro vypuštění:  
  
```MASM  
mov rax, QWORD PTR [ecx]  
mov eax, DWORD PTR [ecx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10d+0100h]  
prefetch [eax]  
movnti rax, QWORD PTR [r8d]  
```  
  
MASM předpokládá, že pokud se zobrazí 32bitový posun samostatně jako operand paměti, 64bitové adresování je určen. Aktuálně neexistuje žádná podpora pro 32-bit adresování s takové operandy.  
  
Nakonec kombinování velikosti zaregistrovat v rámci operandem paměti, jak je ukázáno v následujícím kódu, vygeneruje chybu.  
  
```MASM  
mov eax, DWORD PTR [rcx*2+r10d]  
mov eax, DWORD PTR [ecx*2+r10+0100h]  
```  
  
## <a name="see-also"></a>Viz také  

[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)