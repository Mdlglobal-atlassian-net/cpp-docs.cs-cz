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
ms.openlocfilehash: 4a836bb7bd03bd6654e5c940442fecf541042fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354228"
---
# <a name="accessing-run-time-class-information"></a>Přístup k běhovým informacím o třídě

Tento článek vysvětluje, jak získat přístup k informacím o třídě objektu za běhu.

> [!NOTE]
> Knihovna MFC nepoužívá podporu [informací o typu za běhu](../cpp/run-time-type-information.md) (RTTI) zavedenou v jazyce Visual C++ 4.0.

Pokud jste odvozené třídy z [CObject](../mfc/reference/cobject-class.md) a `IMPLEMENT_DYNAMIC`používá `DECLARE_DYNCREATE` **DECLARE**_**DYNAMIC** a , a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` a makra vysvětlená v článku [Deriving class from CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` třída má schopnost určit přesnou třídu objektu za běhu.

Tato schopnost je nejužitečnější, když je potřeba další typ kontroly argumentů funkce a když je nutné napsat speciální kód založený na třídě objektu. Tento postup se však obvykle nedoporučuje, protože duplikuje funkce virtuálních funkcí.

Členská `CObject` `IsKindOf` funkce může být použita k určení, pokud určitý objekt patří do zadané třídy nebo pokud je odvozen z určité třídy. Argument `IsKindOf` je `CRuntimeClass` objekt, který můžete získat `RUNTIME_CLASS` pomocí makra s názvem třídy.

### <a name="to-use-the-runtime_class-macro"></a>Použití RUNTIME_CLASS makra

1. Použijte `RUNTIME_CLASS` s názvem třídy, jak je `CObject`znázorněno zde pro třídu :

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Zřídka budete potřebovat přístup k objektu třídy run-time přímo. Běžnější použití je předat objekt třídy run-time `IsKindOf` funkci, jak je znázorněno v dalším postupu. Funkce `IsKindOf` testuje objekt, aby zjistila, zda patří do určité třídy.

#### <a name="to-use-the-iskindof-function"></a>Použití funkce IsKindOf

1. Ujistěte se, že třída má podporu třídy run-time. To znamená, že třída musí být odvozena `CObject` přímo nebo nepřímo z `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`používá `DECLARE_SERIAL` **declare**_**DYNAMIC** a `IMPLEMENT_DYNAMIC`, a , nebo a a `IMPLEMENT_SERIAL` makra vysvětlená v článku [Deriving a Class from CObject](../mfc/deriving-a-class-from-cobject.md).

1. Volání `IsKindOf` členské funkce pro objekty této `RUNTIME_CLASS` třídy `CRuntimeClass` pomocí makra ke generování argumentu, jak je znázorněno zde:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf vrátí **hodnotu TRUE,** pokud je objekt členem zadané třídy nebo třídy odvozené ze zadané třídy. `IsKindOf`nepodporuje více dědičnosti nebo virtuální základní třídy, i když můžete použít více dědičnosti pro odvozené třídy Microsoft Foundation v případě potřeby.

Jedním z použití informací o třídě run-time je dynamické vytváření objektů. Tento proces je popsán v článku [Vytvoření dynamického objektu](../mfc/dynamic-object-creation.md).

Podrobnější informace o serializaci a informace o třídě za běhu naleznete v článcích [Soubory v knihovně MFC](../mfc/files-in-mfc.md) a [Serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Použití objektů CObject](../mfc/using-cobject.md)
