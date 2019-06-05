---
title: Editor informací o verzi (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: a17539d0a9fb94c440d65275e9d032182088ae6e
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504489"
---
# <a name="version-information-editor-c"></a>Editor informací o verzi (C++)

Informace o verzi se skládá z společnosti a číslo product ID produktu, číslo verze produktu a oznámení o autorských právech a ochranná známka. S **Editor informací o verzi**, vytvářet a spravovat tato data, která je uložena v prostředku informací o verzi. Prostředku informací o verzi není vyžadována danou aplikací, ale je vhodné místo pro shromažďovat informace, které identifikují aplikaci. Instalační program rozhraní API se také používá informace o verzi.

> [!NOTE]
> Windows standard je jenom jedna verze prostředku s názvem VS_VERSION_INFO.

Prostředku informací o verzi má horní bloku a nejméně jeden menší bloky: jeden blok informací v horní části a jeden nebo více informační bloky verze v dolní části (pro ostatní jazyky a/nebo znakové sady). Začátek bloku má upravitelné číselného pole a vybrat rozevírací seznamy. Menší bloky obsahují pouze upravitelná textová pole.

> [!NOTE]
> Při použití **Editor informací o verzi**, v mnoha případech je můžete kliknout pravým tlačítkem na Zobrazit místní nabídku příkazů specifických pro prostředky. Například pokud jste vybrali při odkazující na položky záhlaví bloku, v místní nabídce ukazuje **nové informace o verzi bloku** a **odstranit blok informací verze** příkazy.

## <a name="how-to"></a>Postupy

**Editor informací o verzi** vám umožní:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi

Vyberte položku jednou zvolit, pak znovu zahajte úprav. Provádět změny přímo ve **informace o verzi** tabulky nebo [okno vlastností](/visualstudio/ide/reference/properties-window). Provedené změny se projeví na obou místech.

Při úpravě `FILEFLAGS` klíče v **Editor informací o verzi**, Všimněte si, že se nedá nastavit **ladění**, **soukromého sestavení**, nebo **speciální sestavení**  vlastnosti **vlastnosti** okno pro soubory .rc:

   - **Editor informací o verzi** nastaví **ladění** vlastnost s `#ifdef` ve skriptu prostředků na základě `_DEBUG` sestavení příznak.

  - Pokud `Private Build` klíč má **hodnotu** nastavit **informace o verzi** tabulce, odpovídající **soukromého sestavení** vlastnost v **vlastnosti**  okně `FILEFLAGS` klíč bude **True**. Pokud **hodnotu** je prázdné, bude vlastnost **False**. Podobně **speciální sestavení** klíče v **informace o verzi** tabulky se váže na **speciální sestavení** vlastnost `FILEFLAGS` klíč.

Můžete řadit informace posloupnost bloku řetězec tak, že vyberete buď **klíč** nebo **hodnotu** záhlaví sloupců. Tyto položky automaticky uspořádat informace do zvolené sekvenci.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Chcete-li přidat informace o verzi pro jiný jazyk (novou verzi informačního bloku)

1. Otevřete poklepáním v prostředku informací o verzi [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Klikněte pravým tlačítkem v tabulce informace o verzi a zvolte **novou verzi informačního bloku**.

   Tento příkaz přidá do aktuálního prostředku informací o verzi z bloku Další informace a otevře se jeho odpovídající vlastnosti v [okno vlastností](/visualstudio/ide/reference/properties-window).

1. V **vlastnosti** okno, vyberte příslušný jazyk a znakové sady pro nový blok.

### <a name="to-delete-a-version-information-block"></a>Odstranění bloku informací o verzi

1. Otevřete poklepáním na ikonu v prostředku informací o verzi [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources).

1. Klikněte pravým tlačítkem na záhlaví bloku, který chcete odstranit a zvolte **odstranit blok informací o verzi**.

   Tento příkaz odstraní vybranou hlavičku a ponechá beze změny zbývající informace o verzi. Akci nelze vrátit zpět.

### <a name="to-access-version-information-from-within-your-program"></a>Přístup k informacím o verzi z programu

Pokud chcete přístup k informacím o verzi z programu, použijte [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) funkce a [Funkce VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) funkce.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Editory prostředků](../windows/resource-editors.md)<br/>
[Nabídky a ostatní prostředky](/windows/desktop/menurc/resources)<br/>
[Informace o verzi (Windows)](/windows/desktop/menurc/version-information)
