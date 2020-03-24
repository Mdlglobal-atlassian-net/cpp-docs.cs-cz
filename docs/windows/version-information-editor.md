---
title: Editor informací o verziC++()
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
ms.openlocfilehash: b083ed27b6b1f471dbec9b96e7be7a6165f8d125
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214367"
---
# <a name="version-information-editor-c"></a>Editor informací o verziC++()

Informace o verzi se skládají z identifikace společnosti a produktu, čísla vydání produktu a autorských práv a oznámení ochranné známky. Pomocí **editoru informací o verzi**můžete vytvořit a spravovat tato data, která jsou uložena v prostředku informací o verzi. Prostředek informace o verzi není vyžadován aplikací, ale je to užitečné místo ke shromáždění informací, které aplikaci identifikují. Rozhraní API pro instalaci používá taky informace o verzi.

> [!NOTE]
> Systém Windows Standard má pouze jeden prostředek verze s názvem VS_VERSION_INFO.

Prostředek informací o verzi má horní blok a jeden nebo více dolních bloků: jeden blok s pevnými informacemi v horním a jednom nebo více blocích s informacemi o verzi v dolní části (pro jiné jazyky a/nebo znakové sady). Horní blok má jak upravitelná číselná pole, tak i rozevírací seznamy s možností výběru. Dolní bloky mají pouze upravitelná textová pole.

> [!NOTE]
> Při použití **editoru informací o verzi**můžete v mnoha případech kliknout pravým tlačítkem myši a zobrazit místní nabídku příkazů specifických pro prostředky. Například pokud vyberete při přechodu na položku hlavičky bloku, místní nabídka zobrazí **nové příkazy blokovat informace o verzi** a **Odstranit informace o blokování verzí** .

## <a name="how-to"></a>Postup

**Editor informací o verzi** vám umožní:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Úprava řetězce v prostředku informací o verzi

Vyberte položku jednou a zvolte ji a pak ji znovu začněte upravovat. Změny proveďte přímo v tabulce **informací o verzi** nebo v [okno Vlastnosti](/visualstudio/ide/reference/properties-window). Změny, které provedete, se projeví na obou místech.

Při úpravách `FILEFLAGS` klíče v **editoru informací o verzi**si všimněte, že v okně **vlastnosti** pro soubory. RC nemůžete nastavit vlastnosti **ladění**, **privátního sestavení**nebo **speciálního sestavení** :

- **Editor informací o verzi** nastavuje vlastnost **ladění** pomocí `#ifdef` ve skriptu prostředků na základě příznaku sestavení `_DEBUG`.

- Pokud má `Private Build` klíč nastavenou **hodnotu** v tabulce **informace o verzi** , bude **true**hodnota odpovídající **privátní vlastnosti sestavení** v okně **vlastnosti** pro `FILEFLAGS` klíč. Pokud je **hodnota** prázdná, vlastnost bude **NEPRAVDA**. Podobně platí, že **speciální klíč sestavení** v tabulce **informací o verzi** je svázán se **speciální vlastností sestavení** pro `FILEFLAGS` klíč.

Můžete seřadit informační sekvenci bloku řetězce tak, že vyberete buď **klíč** , nebo záhlaví sloupců **hodnot** . Tyto nadpisy automaticky změní uspořádání informací do vybrané sekvence.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Přidání informací o verzi pro jiný jazyk (nový blok informací verze)

1. Otevřete prostředek informací o verzi tak, že na něj dvakrát kliknete v [prostředky](how-to-create-a-resource-script-file.md#create-resources).

1. Klikněte pravým tlačítkem v tabulce informace o verzi a vyberte **nový blok informace o verzi**.

   Tento příkaz přidá do aktuálního prostředku informací o verzi další blok informací a otevře odpovídající vlastnosti v [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

1. V okně **vlastnosti** vyberte příslušný jazyk a znakovou sadu pro nový blok.

### <a name="to-delete-a-version-information-block"></a>Odstranění bloku informací o verzi

1. Poklikáním na ikonu v [prostředky](how-to-create-a-resource-script-file.md#create-resources)otevřete prostředek informací o verzi.

1. Klikněte pravým tlačítkem na hlavičku bloku, kterou chcete odstranit, a vyberte **Odstranit blok informací o verzi**.

   Tento příkaz odstraní vybranou hlavičku a zbývající informace o verzi ponechá beze změny. Tuto akci nelze vrátit zpět.

### <a name="to-access-version-information-from-within-your-program"></a>Přístup k informacím o verzi v rámci programu

Chcete-li získat přístup k informacím o verzi v rámci programu, použijte funkci [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) a funkci [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) .

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Nabídky a další prostředky](/windows/win32/menurc/resources)<br/>
[Informace o verzi (Windows)](/windows/win32/menurc/version-information)
