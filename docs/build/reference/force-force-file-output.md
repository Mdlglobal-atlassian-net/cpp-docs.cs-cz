---
title: /FORCE (Vynutit výstup souboru)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: 28b1c21382832c8775ffe0406038a482e74076c5
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299723"
---
# <a name="force-force-file-output"></a>/FORCE (Vynutit výstup souboru)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Poznámky

Možnost/FORCE přikáže linkeru, aby vytvořila platný soubor. exe nebo knihovnu DLL i v případě, že se na symbol odkazuje, ale není definován nebo je definován násobek.

Možnost/FORCE může mít nepovinný argument:

- Pomocí parametru/FORCE: MULTIPLe se vytvoří výstupní soubor bez ohledu na to, zda odkaz vyhledá více než jednu definici pro symbol.

- Pomocí parametru/FORCE: unresolveed lze vytvořit výstupní soubor bez ohledu na to, zda odkaz najde nedefinovaný symbol. /FORCE: nevyřešeno je ignorováno, pokud je symbol vstupního bodu nevyřešený.

/FORCE bez argumentů předpokládá vícenásobné i nevyřešené.

Soubor vytvořený pomocí této možnosti nemusí fungovat podle očekávání. Linker nebude propojen přírůstkově, pokud je zadána možnost/FORCE.

Pokud je modul zkompilován s možností **/CLR**, **/Force** nevytvoří obrázek.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**. 

1. Klikněte na složku **linker** .

1. Klikněte na stránku vlastností **příkazový řádek** .

1. Zadejte možnost do pole **Další možnosti** .

Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
