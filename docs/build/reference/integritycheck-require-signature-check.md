---
title: -INTEGRITYCHECK (vyžaduje Kontrola podpisu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2975f9648415b072c7e0cc893183b4a7880c3e43
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444902"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (povinná kontrola podpisu)

Určuje, že digitální podpis binárního obrazu musí být v okamžiku načtení zkontrolován.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **/INTEGRITYCHECK** je vypnuté.

**/INTEGRITYCHECK** sady možností – v záhlaví PE souboru DLL nebo spustitelný soubor – příznak pro správce paměti pro kontrolu pro digitální podpis načtení obrázku ve Windows. Tato možnost musí být nastavena pro 32bitové i 64bitové knihovny DLL, které implementují kód režimu jádra načtený některými funkcemi Windows a je doporučena pro všechny ovladače zařízení ve Windows Vista, Windows 7, Windows 8, Windows Server 2008 a Windows Server 2012. Verze Windows starší než Windows Vista ignorují tento příznak. Další informace najdete v tématu [vynutit integritu podepisování sady PE (Portable Executable) soubory](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte `/INTEGRITYCHECK` nebo `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)<br/>
[Vynucené soubory Integrity podepisování sady PE (Portable Executable)](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Návod pro podepisování kódu režimu jádra](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[Knihovny AppInit dll ve Windows 7 a Windows serveru 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)