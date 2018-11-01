---
title: /GUARD (povolení kontroly ochrany)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: 730e26477f4684ca6339a25a945ae04ff5a823c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565903"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (povolení kontroly ochrany)

Určuje podporu toku provádění kontrol v spustitelné bitové kopie.

## <a name="syntax"></a>Syntaxe

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Poznámky

Pokud/Guard: CF je zadán, linker změní záhlaví .dll nebo .exe označíte, podpora pro kontroly za běhu Guard toku řízení (CFG). Linker také přidá požadovaný ovládací prvek tok cílové adresy data do záhlaví. / Guard: CF je ve výchozím nastavení zakázána. To může být explicitně zakázat pomocí /GUARD:NO. Aby byla účinná, / Guard: CF také vyžaduje [možnost/DynamicBase (použití adres náhodného generování rozložení prostoru)](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) – možnost linkeru, která je ve výchozím.

Pokud zdrojový kód je zkompilován s použitím [/Guard: CF](../../build/reference/guard-enable-control-flow-guard.md) možnost, kompilátor analyzuje tok řízení prověřením všech nepřímé volání pro možný cíl adresy. Kompilátor vloží kód pro ověření, že je cílová adresa instrukce nepřímé volání v seznamu známých cílové adresy za běhu. Zkontrolujte operační systémy, které podporují parametr CFG zastavte program, který selže CFG runtime. To ztěžuje útočníkovi umožnit pomocí poškození dat. Chcete-li změnit cíl volání nepozorovaně spustit škodlivý kód.

Možnost/Guard: CF musí být zadána kompilátoru a linkeru, aby vytvořil povolené CFG spustitelné bitové kopie. Kód zkompilovat, ale není propojená pomocí/Guard: CF vznikly náklady kontroly za běhu, ale neumožňuje CFG ochrany. Pokud je zadána možnost/Guard: CF do `cl` příkazu kompilujete a propojujete v jednom kroku, kompilátor se předá příznak linkeru. Když **ochrany toku provádění** je nastavena v sadě Visual Studio, je možnost/Guard: CF předány kompilátoru a linkeru. Když souborů objektů nebo knihoven již byly zkompilovány samostatně, možnost musí být explicitně určena v `link` příkazu.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace**, **Linkeru**, **příkazového řádku**.

1. V **další možnosti**, zadejte `/GUARD:CF`.

## <a name="see-also"></a>Viz také

[/guard (povolení ochrany toku řízení)](../../build/reference/guard-enable-control-flow-guard.md)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)