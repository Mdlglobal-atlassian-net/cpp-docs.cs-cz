---
title: "Dva způsoby vytvoření objektu CArchive | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CArchive
dev_langs: C++
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e4243f381d10c3980ba7f819757cf2879e4e8936
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dva způsoby vytvoření objektu CArchive
Existují dva způsoby, jak vytvořit `CArchive` objektu:  
  
-   [Implicitní vytvoření objektu CArchive prostřednictvím rozhraní](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [Explicitní vytvoření objektu CArchive](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Implicitní vytvoření objektu CArchive prostřednictvím rozhraní  
 Nejvíce běžné a nejjednodušší, způsob je umožnit rozhraní vytvořit `CArchive` objekt pro váš dokument jménem uložit, uložit jako a spuštění příkazů v nabídce Soubor.  
  
 Tady je co rozhraní dělá, když uživatel aplikace vydá příkazu Uložit jako v nabídce Soubor:  
  
1.  Uvede **uložit jako** dialogové okno a získá název souboru od uživatele.  
  
2.  Otevře se soubor s názvem uživatel `CFile` objektu.  
  
3.  Vytvoří `CArchive` objekt, který ukazuje na to `CFile` objektu. Při vytváření `CArchive` objektu rozhraní nastaví režim "úložiště" (zápisu, serializovat), a "zatížení" (čtení, deserializovat).  
  
4.  Volání `Serialize` funkci definovanou v vaše **CDocument**-odvozené třídy, předání odkaz na `CArchive` objektu.  
  
 Váš dokument `Serialize` funkce pak zapíše data do `CArchive` objektu, jak je popsáno za chvíli. Po návratu z vaší `Serialize` zničí rozhraní framework funkce, `CArchive` objekt a potom `CFile` objektu.  
  
 Proto pokud necháte rozhraní vytvořit `CArchive` objekt pro dokument, všechny stačí je implementovat dokumentu `Serialize` funkce, která zapisuje a přečte do a z archivu. Máte také implementovat `Serialize` pro žádné `CObject`-odvozené objekty, dokumentu `Serialize` funkce zase serializuje přímo nebo nepřímo.  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a>Explicitní vytvoření objektu CArchive  
 Kromě serializaci dokumentu prostřednictvím rozhraní, jsou k dispozici další situace, kdy může být nutné `CArchive` objektu. Například můžete chtít serializaci dat do a ze schránky, reprezentována `CSharedFile` objektu. Nebo můžete chtít použít uživatelské rozhraní pro uložení souboru, který se liší od toho, které nabízí rozhraní. V takovém případě můžete explicitně vytvořit `CArchive` objektu. Můžete to udělat stejným způsobem, který nemá rozhraní, pomocí následujícího postupu.  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>Explicitní vytvoření objektu CArchive  
  
1.  Vytvořit `CFile` objekt nebo objekt odvozené z `CFile`.  
  
2.  Předat `CFile` objekt, který má v konstruktoru pro `CArchive`, jak je znázorněno v následujícím příkladu:  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     Druhý argument `CArchive` konstruktor je Výčtová hodnota, která určuje, zda archivu se použije pro ukládání nebo načítání dat do nebo ze souboru. `Serialize` Funkce objektu tento stav kontroluje voláním `IsStoring` funkce pro objekt archivu.  
  
 Když skončíte ukládání a načítání dat z nebo `CArchive` objektu, zavřete ji. I když `CArchive` (a `CFile`) objekty se automaticky zavře archivu (a soubor), je dobrým zvykem explicitně tak učinit, protože ho usnadňuje zotavení z chyb. Další informace o zpracování chyb, najdete v článku [výjimkami: zachycení a odstraňování výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
#### <a name="to-close-the-carchive-object"></a>Zavřete objekt CArchive  
  
1.  Následující příklad ukazuje, jak zavřete `CArchive` objektu:  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace objektu](../mfc/serialization-serializing-an-object.md)

