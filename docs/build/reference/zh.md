---
title: /ZH (algoritmus hash pro výpočet kontrolního součtu souboru v ladicích informacích)
description: Použití možnosti kompilátoru/ZH k povolení kontrolních součtů zdrojových souborů MD5, SHA-1 nebo SHA-256 v informacích o ladění
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686871"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH (algoritmus hash pro výpočet kontrolního součtu souboru v ladicích informacích)

Určuje, který šifrovací algoritmus hash se má použít k vygenerování kontrolního součtu každého zdrojového souboru.

## <a name="syntax"></a>Syntaxe

> **/Zh:** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>Argumenty

**/Zh: MD5**\
Pro kontrolní součet použijte hodnotu hash MD5. Tato možnost je výchozí.

**/Zh: SHA1**\
Pro kontrolní součet použijte hodnotu hash SHA-1.

**/Zh: SHA_256**\
Pro kontrolní součet použijte hodnotu hash SHA-256.

## <a name="remarks"></a>Poznámky

Soubory PDB ukládají kontrolní součet pro každý zdrojový soubor kompilovaný do kódu objektu přidruženého spustitelného souboru. Kontrolní součet umožňuje ladicímu programu ověřit, že zdrojový kód, který načte, odpovídá spustitelnému souboru. Kompilátor a ladicí program podporují algoritmy hash MD5, SHA-1 a SHA-256. Ve výchozím nastavení kompilátor k vygenerování kontrolního součtu používá algoritmus hash MD5. Tuto možnost můžete zadat explicitně pomocí možnosti **/zh: MD5** .

Z důvodu rizika kolizí problémů v MD5 a SHA-1 Společnost Microsoft doporučuje použít možnost **/zh: SHA_256** . Hodnota hash SHA-256 může mít za následek malé zvýšení doby kompilace.

Pokud je zadána více než jedna možnost **/zh** , použije se poslední možnost.

Možnost **/zh** je k dispozici počínaje verzí Visual Studio 2019 verze 16,4.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení této možnosti kompilátoru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Nastavte rozevírací seznam **Konfigurace** na **všechny konfigurace**.

1. Vyberte **Vlastnosti konfigurace** > **C/C++**  >  stránka vlastností**příkazového řádku** .

1. Upravte vlastnost **Další možnosti** tak, aby se přidal parametr **/zh: MD5**, **/zh: SHA1**nebo **/zh: SHA_256** , a pak zvolte **OK**.

## <a name="see-also"></a>Další informace najdete v tématech

[Možnosti kompilátoru](compiler-options.md)\
[Zdrojový Server](/windows/win32/debug/source-server-and-source-indexing)
