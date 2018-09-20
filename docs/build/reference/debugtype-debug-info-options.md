---
title: -DEBUGTYPE (Možnosti ladicích informací) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1255c92a7de4a0f1707cd20f91e8b9f1de640942
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440456"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (možnosti ladicích informací)

Možnost /DEBUGTYPE Určuje typ ladicích informací generovaných možnost/Debug.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>Arguments

**CV**<br/>
Přikáže linkeru, aby vygenerovat ladicí informace pro symboly, čísla řádků a další informace o kompilaci objektu do souboru PDB. Ve výchozím nastavení, je tato možnost povolena při **/DEBUG** určena a **/DEBUGTYPE** není zadán.

**PDATA**<br/>
Přikáže linkeru, aby přidat .pdata a .xdata záznamy do datového proudu informace o ladění do souboru PDB. Ve výchozím nastavení, je tato možnost povolena při i **/DEBUG** a **Driver/Driver** jsou zadány možnosti. Pokud **/DEBUGTYPE:PDATA** určena samostatně, linker automaticky zahrne do souboru PDB symboly ladění. Pokud **/DEBUGTYPE:PDATA, oprava** není zadán, linker nezahrnuje ladění symbolů do souboru PDB.

**OPRAVA**<br/>
Přikáže linkeru, aby přidat položky tabulky přemístění do datového proudu informace o ladění do souboru PDB. Ve výchozím nastavení, je tato možnost povolena při i **/DEBUG** a **/PROFILE** jsou zadány možnosti. Pokud **/DEBUGTYPE:FIXUP** nebo **/DEBUGTYPE:FIXUP PDATA** není zadán, linker nezahrnuje ladění symbolů do souboru PDB.

Argumenty, které mají **/DEBUGTYPE** lze kombinovat v libovolném pořadí tak, že je oddělíte čárkou. **/DEBUGTYPE** možnost a její argumenty nejsou velká a malá písmena.

## <a name="remarks"></a>Poznámky

Použití **/DEBUGTYPE** můžete zadat zahrnutí přemístění dat nebo .pdata a .xdata informace v záhlaví tabulky v datovém proudu ladění. To způsobí, že linkeru, aby zahrnul informace o kódu v uživatelském režimu, který se zobrazí v ladicím programu jádra po přerušení v kódu režimu jádra. Aby symboly pro ladění k dispozici při **opravy** je zadán, zahrnují **CV** argument.

Chcete-li ladit kód v uživatelském režimu, což je typické pro aplikace, **/DEBUGTYPE** možnost není potřebná. Ve výchozím nastavení, přepínače kompilátoru určující ladění výstupu ([/Z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) vygenerovat všechny informace potřebné pomocí sady Visual Studio debugger. Použití **/DEBUGTYPE:PDATA** nebo **chyby, PDATA, oprava** ladit kód, který kombinuje uživatelského režimu a režimu jádra součásti, jako je například konfigurace aplikace pro ovladače zařízení. Další informace o režimu jádra ladicích programů, naleznete v tématu [ladění nástroje pro Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>Viz také

[/DEBUG (generování informací o ladění)](../../build/reference/debug-generate-debug-info.md)<br/>
[/DRIVER (ovladač režimu jádra Windows NT)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE (profiler nástrojů pro měření výkonu)](../../build/reference/profile-performance-tools-profiler.md)<br/>
[Ladicí nástroje pro Windows (WinDbg, KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)