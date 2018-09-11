---
title: Binární Editor (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary.F1
dev_langs:
- C++
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 86dd69a893c589ad4ebba06c2577925eae959f40
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313688"
---
# <a name="binary-editor-c"></a>Binární Editor (C++)

> [!WARNING]
> **Binární Editor** není k dispozici ve verzích Express.

Binární editor umožňuje upravovat libovolný prostředek na binární úrovni v šestnáctkovém formátu nebo ve formátu ASCII. Můžete také použít [najít – příkaz](/visualstudio/ide/reference/find-command) k vyhledání řetězce ASCII nebo šestnáctkové bajty. Měli byste použít **binární** editor jenom v případě, že potřebujete zobrazit nebo provést menší změny vlastní prostředky nebo typy prostředků nejsou podporovány prostředím Visual Studio.

Otevřete **binární Editor**, zvolte nejprve **souboru** > **nový** > **souboru** v hlavní nabídce vyberte soubor, kterou chcete upravit a potom klikněte na rozevírací šipku vedle položky **otevřít** a tlačítko **otevřít v** > **binární Editor**.

> [!CAUTION]
> Úprava prostředků jako dialogová okna, obrázky nebo nabídky pomocí binárního editoru není bezpečná. Nesprávné úpravy mohou prostředek poškodit a učinit jej nečitelným v jeho nativním editoru.

> [!TIP]
> Při použití **binární** editoru v mnoha případech je můžete kliknout pravým tlačítkem na Zobrazit místní nabídku příkazů specifických pro prostředky. Dostupné příkazy závisí na položce, na kterou právě ukazuje kurzor. Například pokud klepnete na tlačítko při přejdete **binární** editor se zvolenými šestnáctkovými hodnotami, v místní nabídce se zobrazuje **Vyjmout**, **kopírování**, a **vložit**  příkazy.

S **binární** editoru, můžete:

- [Otevření prostředku pro binární úpravy](../windows/opening-a-resource-for-binary-editing.md)

- [Upravovat binární data](../windows/editing-binary-data.md)

- [Vyhledat binární data](../windows/finding-binary-data.md)

- [Vytvořit nový vlastní nebo datový prostředek](../windows/creating-a-new-custom-or-data-resource.md)

## <a name="managed-resources"></a>Spravované prostředky

Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a **binární** editor pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)