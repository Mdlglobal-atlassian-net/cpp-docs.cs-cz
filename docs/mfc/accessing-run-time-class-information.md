---
title: Přístup k běhovým informacím o třídě
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 061cc04857b0d1763fb4ee975912bcca1b9d014f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455272"
---
# <a name="accessing-run-time-class-information"></a>Přístup k běhovým informacím o třídě

Tento článek vysvětluje, jak získat přístup k informacím o třídě objektu v době běhu.

> [!NOTE]
>  Knihovny MFC nepoužívá [informace o typu za běhu](../cpp/run-time-type-information.md) zavedena v aplikaci Visual C++ 4.0 podpory (RTTI).

Pokud mají odvozené třídě z [CObject](../mfc/reference/cobject-class.md) a použít **DECLARE**_**dynamické** a `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra je popsáno v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` třída má schopnost určit přesné třídu objektu v době běhu.

Tato možnost je nejužitečnější, když je potřeba další kontrolu argumentů funkce typu a při psaní kódu zvláštní účely na základě třídy objektu. Tento postup však není obvykle doporučeno, protože duplikuje fungování virtuálních funkcí.

`CObject` Členskou funkci `IsKindOf` je možné určit, jestli konkrétní objekt náleží do dané třídy, nebo pokud je odvozena z určité třídy. Argument `IsKindOf` je `CRuntimeClass` objektu, který můžete získat pomocí `RUNTIME_CLASS` – makro s názvem třídy.

### <a name="to-use-the-runtimeclass-macro"></a>Použití makra RUNTIME_CLASS

1. Použití `RUNTIME_CLASS` s názvem třídy, jak je znázorněno zde pro třídu `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Musíte jen zřídka přímý přístup k objektu třídy za běhu. Běžnější použití je předat objekt run-time třída `IsKindOf` fungovat, jak je znázorněno v následujícím postupu. `IsKindOf` Otestuje objekt zobrazit, jestli patří do určité třídy.

#### <a name="to-use-the-iskindof-function"></a>Chcete-li použít funkci IsKindOf

1. Ujistěte se, že třída má podpora run-time třída. To znamená, třída musí mít byla odvozena přímo nebo nepřímo z `CObject` a použít **DECLARE**_**dynamické** a `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra je popsáno v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md).

1. Volání `IsKindOf` členské funkce pro objekty třídy, pomocí `RUNTIME_CLASS` – makro ke generování `CRuntimeClass` argument, jak je znázorněno zde:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  Vrátí IsKindOf **TRUE** Pokud objekt je členem dané třídy nebo třídy odvozené z dané třídy. `IsKindOf` nepodporuje více dědičnosti nebo virtuálními základními třídami, i když používáte vícenásobné dědičnosti pro odvozených tříd Microsoft Foundation classes v případě potřeby.

Jedno použití informací o třídě za běhu spočívá ve vytvoření dynamické objektů. Tento proces je popsán v článku [vytváření dynamických objektů](../mfc/dynamic-object-creation.md).

Další podrobné informace o serializaci a informace o třídě za běhu, najdete v článcích [soubory v prostředí MFC](../mfc/files-in-mfc.md) a [serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Použití objektů CObject](../mfc/using-cobject.md)

