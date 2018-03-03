---
title: "Odvození třídy z objektu CObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 97e151d8c3ec44286807baf5e68d4e4eac17e306
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deriving-a-class-from-cobject"></a>Odvození třídy z objektu CObject
Tento článek popisuje minimální kroky potřebné k odvození třídy z [CObject](../mfc/reference/cobject-class.md). Další `CObject` třída články popisují kroky potřebné k využít výhod konkrétní `CObject` funkce, jako je serializace a diagnostiky podporu ladění.  
  
 V otázkách, `CObject`, se často používají podmínky "soubor rozhraní" a "implementace soubor". Soubor rozhraní (často říká soubor hlaviček, nebo. Soubor H) obsahuje deklaraci třídy a všechny ostatní informace, které jsou potřeba k použití třídy. Soubor implementace (nebo. Soubor CPP) obsahuje definice třídy, jakož i kód, který implementuje členské funkce tříd. Například pro třídu s názvem `CPerson`, vytvořili byste obvykle soubor rozhraní s názvem osoby. H a implementace soubor s názvem osoby. CPP. Pro některé malé třídy, které nebude sdílené mezi aplikacemi, je však někdy usnadňují kombinace rozhraní a implementaci do jednoho. Soubor CPP.  
  
 Můžete zvolit ze čtyř úrovní funkčnosti při odvození třídy z `CObject`:  
  
-   Základní funkce: žádná podpora pro run-time třída informace nebo serializace ale zahrnuje Správa diagnostiky paměti.  
  
-   Základní funkce a podporu run-time třída informace.  
  
-   Základní funkce a podporu run-time třída informace a dynamického vytváření.  
  
-   Základní funkce a podporu pro run-time třída informace, dynamických a serializace.  
  
 Třídy pro opakované použití (ty, které později bude sloužit jako základní třídy) by měla obsahovat alespoň run-time třída podporu a podporu serializace, pokud se očekává nutnosti budoucí serializace.  
  
 Vyberte úroveň funkčnosti pomocí konkrétní deklaraci a implementaci makra v deklaraci a implementaci odvozujete od třídy `CObject`.  
  
 Následující tabulka znázorňuje vztah mezi makra použít pro podporu serializace a informace o běhu.  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra používá k serializaci a informace o běhu  
  
|Použít – makro|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|Základní `CObject` funkce|Ne|Ne|Ne|  
|`DECLARE_DYNAMIC`|Ano|Ne|Ne|  
|`DECLARE_DYNCREATE`|Ano|Ano|Ne|  
|`DECLARE_SERIAL`|Ano|Ano|Ano|  
  
#### <a name="to-use-basic-cobject-functionality"></a>Použití funkce základní třídy CObject  
  
1.  Použijte normální syntaxi C++ odvození třídě z `CObject` (nebo z třídy odvozené od `CObject`).  
  
     Následující příklad ukazuje nejjednodušším případě odvození třídy z `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 Za normálních okolností však můžete přepsat některé `CObject`na členské funkce pro zpracování jsou specifikace novou třídu. Například, obvykle můžete přepsat `Dump` funkce `CObject` zajistit výstupu ladění pro obsah vaší třídy. Podrobnosti ohledně postupu přepsání `Dump`, najdete v článku [diagnostiky: vypsání obsah objektu](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59). Můžete také přepsat `AssertValid` funkce `CObject` poskytnout vlastní testování k ověření konzistence dat členů třídy objektů. Popis toho, jak lze přepsat `AssertValid`, najdete v části [assert_valid – MFC a CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6).  
  
 Článek [určení úrovní funkčnosti](../mfc/specifying-levels-of-functionality.md) popisuje, jak určit jiných úrovních funkčnosti, včetně informací o run-time třída, vytváření dynamických objektů a serializace.  
  
## <a name="see-also"></a>Viz také  
 [Použití objektů CObject](../mfc/using-cobject.md)

