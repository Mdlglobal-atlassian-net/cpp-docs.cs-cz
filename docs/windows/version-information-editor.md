---
title: Editor informací o verzi (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version.F1
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: 817092af316fbc39b696e1ed19e1c67f9a799bd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667490"
---
# <a name="version-information-editor-c"></a>Editor informací o verzi (C++)

Informace o verzi se skládá z společnosti a číslo product ID produktu, číslo verze produktu a oznámení o autorských právech a ochranná známka. S **informace o verzi** editoru lze vytvářet a spravovat tato data, která je uložena v prostředku informací o verzi. Prostředku informací o verzi není vyžadována danou aplikací, ale je vhodné místo pro shromažďovat informace, které identifikují aplikaci. Instalační program rozhraní API se také používá informace o verzi.

Prostředku informací o verzi má horní bloku a nejméně jeden menší bloky: jeden blok informací v horní části a jeden nebo více informační bloky verze v dolní části (pro ostatní jazyky a/nebo znakové sady). Začátek bloku má upravitelné číselného pole a vybrat rozevírací seznamy. Menší bloky obsahují pouze upravitelná textová pole.

> [!NOTE]
> Windows standard je jenom jedna verze prostředku s názvem VS_VERSION_INFO.

**Informace o verzi** editor umožňuje:

- [Úprava řetězce v prostředku informací o verzi](../windows/editing-a-string-in-a-version-information-resource.md)

- [Přidání informací o verzi pro jiný jazyk (novou verzi informačního bloku)](../windows/adding-version-information-for-another-language.md)

- [Odstranění bloku informací o verzi](../windows/deleting-a-version-information-block.md)

- [O přístup k verzi z programu](../windows/accessing-version-information-from-within-your-program.md)

   > [!NOTE]
   > Při použití **informace o verzi** editoru v mnoha případech můžete kliknout pravým tlačítkem na Zobrazit místní nabídku příkazů specifických pro prostředky. Například vyberete-li při odkazující na položky záhlaví bloku, v místní nabídce se zobrazuje **nové informace o verzi bloku** a **odstranit blok informací verze** příkazy.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)