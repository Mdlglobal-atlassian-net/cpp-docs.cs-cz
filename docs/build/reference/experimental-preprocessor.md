---
title: '/Experimental: preprocesor (povolit režim shody preprocesoru)'
description: 'Použijte možnost kompilátoru/Experimental: preprocesor, chcete-li povolit experimentální podporu kompilátoru pro standardní vyhovující preprocesor.'
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754040"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/Experimental: preprocesor (povolit režim shody preprocesoru)

Tato možnost umožňuje experimentálního preprocesoru založeného na tokenech, který se podrobněji vyhovuje standardům C++ 11, včetně funkcí preprocesoru C99. Další informace najdete v tématu [MSVC experimentální preprocesor – přehled](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntaxe

> **/Experimental: preprocesor**[ **-** ]

## <a name="remarks"></a>Poznámky

Použijte možnost kompilátoru **/Experimental: preprocesor** pro povolení experimentálního vyhovujícího preprocesoru. Můžete použít **/Experimental: preprocesor –** možnost k explicitnímu určení tradičního preprocesoru.

Možnost **/Experimental: preprocesor** je k dispozici počínaje verzí Visual Studio 2017 verze 15,8.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránce vlastností **příkazového řádku** **jazyka C/C++**  > .

1. Upravte vlastnost **Další možnosti** tak, aby zahrnovala **/Experimental: preprocesor** a pak zvolte **OK**.

## <a name="see-also"></a>Viz také:

[/Zc (shoda)](zc-conformance.md)
