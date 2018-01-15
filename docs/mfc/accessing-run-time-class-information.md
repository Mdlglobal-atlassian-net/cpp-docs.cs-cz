---
title: "Přístup k informacím o Run-Time třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b74c76e5cc156d106f8358fe729df0bb7026422
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-run-time-class-information"></a>Přístup k běhovým informacím o třídě
Tento článek vysvětluje, jak pro přístup k informacím o třídě objektu v době běhu.  
  
> [!NOTE]
>  MFC nepoužívá [informací o typu Run-Time](../cpp/run-time-type-information.md) podporu (RTTI) byla zavedená v aplikaci Visual C++ 4.0.  
  
 Pokud mají odvozené třídě z [CObject](../mfc/reference/cobject-class.md) a použít **DECLARE**_**dynamické** a `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra popsané v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md), `CObject` třída má schopnost určit přesnou třídu objektu v době běhu.  
  
 Tato možnost je velmi užitečné, když je potřeba další typ kontroly argumenty funkce a když musíte napsat kód speciální na základě třídy objektu. Tento postup však se většinou nedoporučuje, protože duplikuje funkci virtuální funkce.  
  
 `CObject` – Členská funkce `IsKindOf` lze použít k určení, pokud daný objekt patří do zadané třídy, nebo pokud je odvozený od určité třídy. Argument `IsKindOf` je `CRuntimeClass` objekt, který můžete získat pomocí `RUNTIME_CLASS` makro s názvem třídy.  
  
### <a name="to-use-the-runtimeclass-macro"></a>Použití makra RUNTIME_CLASS  
  
1.  Použití `RUNTIME_CLASS` s názvem třídy, jak je vidět tady pro třídu `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]  
  
 Musíte se zřídka přímo přistupovat k tomuto objektu run-time třída. Více běžně používá, je předat run-time třída objekt, který má `IsKindOf` fungovat, jak je vidět v dalším postupu. `IsKindOf` Funkce testy objekt zobrazit, pokud patří do určité třídy.  
  
#### <a name="to-use-the-iskindof-function"></a>Použití iskindof – funkce  
  
1.  Ujistěte se, že má třída podporu run-time třída. To znamená, třída musí pocházet přímo nebo nepřímo ze `CObject` a použít **DECLARE**_**dynamické** a `IMPLEMENT_DYNAMIC`, `DECLARE_DYNCREATE` a `IMPLEMENT_DYNCREATE`, nebo `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra popsané v článku [odvození třídy z objektu CObject](../mfc/deriving-a-class-from-cobject.md).  
  
2.  Volání `IsKindOf` – členská funkce pro objekty třídy, pomocí `RUNTIME_CLASS` makro ke generování `CRuntimeClass` argument, jak je vidět tady:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]  
  
     [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]  
  
    > [!NOTE]
    >  Vrátí IsKindOf **TRUE** Pokud se objekt členem pro zadanou třídu nebo třídy odvozené od pro zadanou třídu. `IsKindOf`nepodporuje více dědičnosti nebo virtuální základní třídy, přestože je možné použít vícenásobná dědičnost pro vaše odvozené třídy Microsoft Foundation v případě potřeby.  
  
 Jedno použití informace run-time třída je v dynamického vytváření objektů. Tento proces je popsána v článku [dynamické vytvoření objektu](../mfc/dynamic-object-creation.md).  
  
 Podrobnější informace o serializaci a run-time třída informace najdete v článcích [soubory v prostředí MFC](../mfc/files-in-mfc.md) a [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití objektů CObject](../mfc/using-cobject.md)

