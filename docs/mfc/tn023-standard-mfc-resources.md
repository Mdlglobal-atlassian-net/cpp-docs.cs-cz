---
title: 'TN023: Standardní prostředky MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: 90e7b9b7c354ba919c3dee279725b4498bea57ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370385"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: Standardní prostředky MFC

Tato poznámka popisuje standardní prostředky poskytované a potřebné knihovny knihovny knihovny Knihovny MFC.

## <a name="standard-resources"></a>Standardní zdroje

Knihovna MFC nabízí dvě kategorie předdefinovaných prostředků, které můžete použít ve vaší aplikaci: prostředky klipartu a standardní rámcové prostředky.

Prostředky klipartu jsou další prostředky, na kterých rozhraní nezávisí, ale které můžete chtít přidat do uživatelského rozhraní aplikace. Následující zdroje klipartu jsou obsaženy ve vzorku [clipartu](../overview/visual-cpp-samples.md)MFC General :

- Common.rc: Jeden soubor prostředků, který obsahuje:

  - Velká kolekce ikon, které představují různé obchodní a úlohy zpracování dat.

  - Několik běžných kurzorů (viz také Afxres.rc).

  - Bitmapa panelu nástrojů, která obsahuje několik tlačítek panelu nástrojů.

  - Rastrové a ikonové prostředky používané souborem Commdlg.dll.

- Indicate.rc: Obsahuje prostředky řetězce pro indikátory stavového řádku stavu stavu, například "CAP" pro caps lock.

- Prompts.rc: Obsahuje prostředky řetězce s výzvou nabídky pro každý předdefinovaný příkaz, například "Vytvořit nový dokument" pro ID_FILE_NEW.

- Commdlg.rc: Soubor .rc kompatibilní s visual c++, který obsahuje standardní šablony dialogů COMMDLG.

Standardní framework prostředky jsou prostředky s ID definované AFX, které framework závisí na pro interní implementace. Tyto prostředky definované afx bude zřídka nutné změnit. Pokud tak učiníte, měli byste postupovat podle postupu popsaného dále v tomto tématu.

Následující prostředky architektury jsou obsaženy v adresáři Knihovna MFC\INCLUDE:

- Afxres.rc: Společné zdroje používané v rámci.

- Afxprint.rc: Zdroje specifické pro tisk.

- Afxolecl.rc: Prostředky specifické pro klientské aplikace OLE.

- Afxolev.rc: Prostředky specifické pro úplné serverové aplikace OLE.

## <a name="using-clip-art-resources"></a>Použití zdrojů klipartu

#### <a name="to-use-a-clip-art-binary-resource"></a>Použití klipartového binárního prostředku

1. Otevřete soubor prostředků aplikace v jazyce Visual C++.

1. Otevřít Common.rc. Tento soubor obsahuje všechny binární klipartové prostředky. To může nějakou dobu trvat, protože soubor Common.rc je kompilován.

1. Při přetahování prostředků z souboru Common.rc do souboru prostředků aplikace podržte klávesu CTRL.

Chcete-li použít jiné prostředky klipartu, postupujte stejným způsobem. Jediným rozdílem je, že otevřete příslušný soubor RC namísto Common.rc.

> [!NOTE]
> Dávejte pozor, abyste neúmyslně přesunout prostředky z Common.rc trvale. Pokud při přetahování prostředků podržíte klávesu CTRL, vytvoříte kopii. Pokud při tažení nepodržíte klávesu CTRL, budou prostředky přesunuty. Pokud se obáváte, že jste omylem provedli změny v souboru Common.rc, klepněte na tlačítko "Ne", když budete dotázáni, zda chcete uložit změny common.rc.

> [!NOTE]
> Soubory prostředků RC mají v nich speciální prostředek TEXTINCLUDE, který vám zabrání nechtěnému uložení nad standardními soubory RC.

### <a name="customizing-standard-framework-resources"></a>Přizpůsobení prostředků standardu frameworku

Standardní framework prostředky jsou obvykle zahrnuty v aplikaci pomocí příkazu #include v souboru prostředků aplikace. AppWizard vygeneruje soubor prostředků. Tento soubor obsahuje příslušné standardní framework prostředky, v závislosti na možnosti AppWizard, které vyberete. Můžete zkontrolovat, přidat nebo odebrat prostředky, které jsou zahrnuty změnou direktivy kompilace. Chcete-li to provést, otevřete nabídku **Zdroj** a vyberte **možnost Nastavit zahrnuje**. Podívejte se na položku úprav "Direktivy v době kompilace". Příklad:

```
#include "afxres.rc"
#include "afxprint.rc"
```

Nejběžnější případ přizpůsobení prostředků standardní architektury je přidání nebo odebrání dalších zahrnuje pro tisk, OLE klienta a ole server podporu.

V některých výjimečných případech můžete chtít přizpůsobit obsah standardních prostředků rozhraní framework pro konkrétní aplikaci, nikoli pouze přidat a odebrat celý soubor. Následující kroky ukazují, jak můžete omezit prostředky, které jsou zahrnuty:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Přizpůsobení obsahu standardního souboru prostředků

1. Otevřete soubor prostředků ve Visual C++.

1. Pomocí příkazu Sada prostředků `#include` Zahrnuje odeberte standardní soubor RC, který chcete přizpůsobit. Chcete-li například přizpůsobit panel nástrojů náhledu tisku, odeberte `#include "afxprint.rc"` řádek.

1. Otevřete příslušné soubory standardních prostředků v knihovně MFC\INCLUDE. Následující příklad dříve v tomto tématu, příslušný soubor je MFC\Include\Aafxprint.rc

1. Zkopírujte všechny prostředky ze standardního souboru RC do souboru prostředků aplikace.

1. Upravte kopii standardních prostředků v souboru prostředků aplikace.

> [!NOTE]
> Neupravujte prostředky přímo ve standardních souborech RC. Tím se změní prostředky, které jsou k dispozici v každé aplikaci, nikoli pouze v té, na které právě pracujete.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
