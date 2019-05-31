---
title: /INTEGRITYCHECK (povinná kontrola podpisu)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: a46f31140c01753fdaa6e72fd0f741f569a5ad94
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450441"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (povinná kontrola podpisu)

Určuje, že digitální podpis binárního obrazu musí být v okamžiku načtení zkontrolován.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **/INTEGRITYCHECK** je vypnuté.

**/INTEGRITYCHECK** sady možností – v záhlaví PE souboru DLL nebo spustitelný soubor – příznak pro správce paměti pro kontrolu pro digitální podpis načtení obrázku ve Windows. Tato možnost musí být nastavena pro 32bitové i 64bitové knihovny DLL, které implementují kód režimu jádra načtený některými funkcemi Windows a je doporučena pro všechny ovladače zařízení ve Windows Vista, Windows 7, Windows 8, Windows Server 2008 a Windows Server 2012. Verze Windows starší než Windows Vista ignorují tento příznak. Další informace najdete v tématu [vynutit integritu podepisování sady PE (Portable Executable) soubory](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte `/INTEGRITYCHECK` nebo `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[Vynucené soubory Integrity podepisování sady PE (Portable Executable)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Návod pro podepisování kódu režimu jádra](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[Knihovny AppInit dll ve Windows 7 a Windows serveru 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)
