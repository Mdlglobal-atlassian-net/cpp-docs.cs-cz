---
title: /INTEGRITYCHECK (povinná kontrola podpisu)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492849"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (povinná kontrola podpisu)

Určuje, že digitální podpis binárního obrázku musí být zkontrolován v době načítání.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je **/INTEGRITYCHECK** vypnutý.

Možnost **/INTEGRITYCHECK** nastaví – v hlavičce PE souboru DLL nebo spustitelného souboru – příznak pro správce paměti, který zkontroluje digitální podpis, aby se načetla bitová kopie v systému Windows. Tato možnost musí být nastavena pro 32 i pro 64 bitové knihovny DLL, které implementují kód režimu jádra načtený některými funkcemi systému Windows, a je doporučena pro všechny ovladače zařízení v systémech Windows Vista, Windows 7, Windows 8, Windows Server 2008 a Windows Server 2012. Verze systému Windows starší než Windows Vista tento příznak ignoruje. Další informace najdete v tématu [vynucené podepisování integrity souborů PE (Portable executable)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte uzel **Vlastnosti konfigurace** .

1. Rozbalte uzel **linker** .

1. Vyberte stránku vlastností **příkazový řádek** .

1. V **dalších možnostech**zadejte `/INTEGRITYCHECK` nebo `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[Vynucené podepisování integrity souborů PE (Portable executable)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Požadavky na podepisování kódu v režimu jádra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[AppInit dll a zabezpečené spouštění](/windows/win32/dlls/secure-boot-and-appinit-dlls)
