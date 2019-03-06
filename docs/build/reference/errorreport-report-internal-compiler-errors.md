---
title: /errorReport (sestava s interními chybami kompilátoru)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 70df0f99ccac91ef8b7651faf3c93bb2971fb904
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414548"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (sestava s interními chybami kompilátoru)

Umožňuje poskytnout informace o kompilátoru vnitřní chybě (ICE) přímo společnosti Microsoft.

## <a name="syntax"></a>Syntaxe

```
/errorReport:[ none | prompt | queue | send ]
```

## <a name="arguments"></a>Arguments

**None**<br/>
Sestavy o vnitřních chybách kompilátoru nebudou shromážděné nebo odeslané společnosti Microsoft.

**prompt**<br/>
Zobrazí výzvu k odeslání hlášení, pokud obdržíte chybu kompilátoru. **řádek** výchozí nastavení je při kompilaci aplikace ve vývojovém prostředí.

**fronty**<br/>
Zařadí do fronty zprávy o chybách. Při přihlašování s použitím oprávnění správce, takže můžete nahlásit všechny chyby od posledního byly zaznamenány v, zobrazí se okno (nezobrazí se výzva k odeslání zprávy o chybách více než jednou za tři dny). **fronty** výchozí nastavení je při kompilaci aplikace příkazového řádku.

**Odeslat**<br/>
Automaticky odesílá zprávy o vnitřních chybách kompilátoru společnosti Microsoft, pokud vytváření sestav je povolené nastavení systému Windows zasílání zpráv o chybách.

## <a name="remarks"></a>Poznámky

Vnitřní chyba kompilátoru (ICE) výsledky, když kompilátor nemůže zpracovat soubor zdrojového kódu. Pokud dojde k ICE, kompilátor nevytvoří výstupní soubor nebo užitečnou diagnostiku, která můžete použít jak kód opravit.

V dřívějších verzích když jste se dostali ICE jste ukončena. doporučujeme volat Microsoft Product Support Services nahlásit problém. S **/errorreport**, můžete zadat informace ICE přímo společnosti Microsoft. Zprávy o chybách můžete zvýšit kompilátoru budoucích verzí.

Uživatele umožňuje odeslat sestavy závisí na oprávnění zásad počítače a uživatele.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **C/C++** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **zpráv o chybách** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
