---
title: "TN002: Formát dat trvalých objektů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca6a78f19b43ded59efb56b87f9fe3f44887a31a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formát dat trvalých objektů
Tato poznámka popisuje MFC rutiny, které podporují trvalé objekty C++ a formát data objektu, když je uložena v souboru. Vztahuje se pouze na tříd pomocí [declare_serial –](../mfc/reference/run-time-object-model-services.md#declare_serial) a [implement_serial –](../mfc/reference/run-time-object-model-services.md#implement_serial) makra.  
  
## <a name="the-problem"></a>Problém  
 Implementace MFC trvalých dat ukládá data pro mnoho objektů v jednom souvislé části souboru. Objektu `Serialize` metoda převádí data objektu na kompaktní binární formát.  
  
 Implementace zaručuje, že všechna data uložena ve stejném formátu pomocí [CArchive – třída](../mfc/reference/carchive-class.md). Používá `CArchive` objektu jako převaděče. Tento objekt potrvají od okamžiku se vytvoří, dokud zavoláte [CArchive::Close](../mfc/reference/carchive-class.md#close). Tuto metodu lze volat explicitně programátorem nebo implicitně destruktoru při ukončení programu obor, který obsahuje `CArchive`.  
  
 Tato poznámka popisuje provádění `CArchive` členy [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Najdete kód pro tyto funkce v Arcobj.cpp a hlavní implementaci pro `CArchive` v Arccore.cpp. Uživatelský kód nevyvolá `ReadObject` a `WriteObject` přímo. Místo toho používají tyto objekty specifické pro třídu bezpečnost typů vložení a extrakce operátory, které jsou automaticky generovány `DECLARE_SERIAL` a `IMPLEMENT_SERIAL` makra. Následující kód ukazuje, jak `WriteObject` a `ReadObject` se implicitně označují jako:  
  
```  
class CMyObject : public CObject  
{  
    DECLARE_SERIAL(CMyObject) 
};  
 
IMPLEMENT_SERIAL(CMyObj, CObject, 1)  
 
// example usage (ar is a CArchive&)  
CMyObject* pObj;  
CArchive& ar;  
ar <<pObj;        // calls ar.WriteObject(pObj)  
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))  
```  
  
## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Ukládání objektů do úložiště (CArchive::WriteObject)  
 Metoda `CArchive::WriteObject` zapíše hlavičky data, která se používá k rekonstrukci objektu. Tato data se skládá ze dvou částí: typ objektu a stav objektu. Tato metoda je také odpovědné za údržbu identitu objektu zapisovaný out, aby se uložily pouze jedné kopie, bez ohledu na počet ukazatele na tento objekt (včetně cyklické ukazatele).  
  
 Ukládání (vkládání) a obnovení (extrakce) objektů spoléhá na několik "manifestu konstanty." Jsou hodnoty, které se ukládají v binárním a obsahují důležité informace do archivu (Všimněte si, že předpona "w" Určuje množství 16bitové):  
  
|Značka|Popis|  
|---------|-----------------|  
|wNullTag|Použít pro ukazatelů objekt s hodnotou NULL (0).|  
|wNewClassTag|Označuje, že třída popis, který následuje je nového pro tento kontext archivu (-1).|  
|wOldClassTag|Označuje, že třídu objektu, který je čten ukázala v tomto kontextu (0x8000).|  
  
 Při ukládání objektů, archivu udržuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( `m_pStoreMap`) tedy mapování z objekt uložené na trvalé identifikátor 32-bit (PID). PID je přiřazený k každý jedinečný objekt a každý název jedinečný třídy, který je uložený v rámci archivu. Tyto PID jsou předat postupně začínajícím hodnotou 1. Tyto PID nemají žádný význam mimo obor archivu a zejména jsou Nezaměňovat s záznam čísel nebo jiných položek identity.  
  
 V `CArchive` třídy, PID jsou 32-bit, ale jsou dokud je větší než 0x7FFE zapsány jako 16bitové. Velké PID se zapisují jako 0x7FFF, za nímž následuje identifikátor PID 32-bit. Tím se zachová kompatibilitu s projekty, které byly vytvořené v dřívějších verzích.  
  
 Po odeslání žádosti se uložit objekt do archivu (obvykle pomocí operátoru globální vložení) s hodnotou NULL se provádí kontrolu [CObject](../mfc/reference/cobject-class.md) ukazatel. Pokud je ukazatel NULL, `wNullTag` se vloží do archivní datový proud.  
  
 Pokud je ukazatel není NULL a serializovat se dají (třída je `DECLARE_SERIAL` – třída), zkontroluje kód `m_pStoreMap` zobrazíte, zda objekt byl již uložen. Pokud ano, vloží kód PID 32-bit spojené s tímto objektem do archivní datový proud.  
  
 Pokud objekt ještě nebyl uložen před, máte dvě možnosti ke zvážení: buď objekt a přesný typ objektu (třídy) jsou nové pro tento kontext archivu, nebo objekt je už viděli přesně typu. K určení, zda typ ukázala, kód dotazy `m_pStoreMap` pro [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objekt, který odpovídá `CRuntimeClass` objekt přidružený k objektu. Pokud není nalezena shoda, `WriteObject` vloží značku, která je bitového `OR` z `wOldClassTag` a tento index. Pokud `CRuntimeClass` je pro tento kontext archivu nová `WriteObject` přiřadí nový PID třídy a vloží ho do archivu, před sebou `wNewClassTag` hodnotu.  
  
 Popisovač pro tuto třídu se pak vloží do archivu pomocí `CRuntimeClass::Store` metoda. `CRuntimeClass::Store`Vloží číslo schématu třídy (viz níže) a název text ASCII třídy. Všimněte si, že použití názvu text ASCII nezaručuje jedinečnosti archivu napříč aplikacemi. Proto by mělo být označení datové soubory do zabránit poškození. Následující vkládání informace o třídě archivu převádí objekt do `m_pStoreMap` a potom zavolá `Serialize` metoda vložit data specifická pro třídu. Objekt do umístění `m_pStoreMap` před voláním `Serialize` brání více kopií objektu, neuloží se do úložiště.  
  
 Při vracení na počáteční volající (obvykle kořen síťových objektů), musí volat [CArchive::Close](../mfc/reference/carchive-class.md#close). Pokud máte v plánu k dalším [cfile –](../mfc/reference/cfile-class.md)operace, je třeba zavolat `CArchive` metoda [vyprázdnění](../mfc/reference/carchive-class.md#flush) zabránit poškození archivu.  
  
> [!NOTE]
>  Tato implementace ukládá pevný limit 0x3FFFFFFE indexů podle kontextu archivu. Toto číslo představuje maximální počet jedinečných objekty a třídy, které lze uložit do jednoho archivu, ale soubor jeden disk může mít neomezený počet kontexty archivu.  
  
## <a name="loading-objects-from-the-store-carchivereadobject"></a>Načítání objektů z úložiště (CArchive::ReadObject)  
 Načítání (extrahování) používá objekty `CArchive::ReadObject` metoda a je konverzace z `WriteObject`. Stejně jako u `WriteObject`, `ReadObject` není volán přímo z uživatelského kódu; uživatelského kódu by měly volat bezpečnost typů extrakce operátor, který volá `ReadObject` s očekávané `CRuntimeClass`. Díky tomu se budou integritu typ operace extrakce.  
  
 Vzhledem k tomu `WriteObject` implementace přiřazené roste PID, počínaje 1 (0 je předdefinovaná jako objekt NULL), `ReadObject` implementace můžete použít pole pro uchování stavu kontextu archivu. Když je PID číst z úložiště, pokud kód PID je větší než aktuální horní mez `m_pLoadArray`, `ReadObject` ví, že dodržuje nový objekt (nebo popis třídy).  
  
## <a name="schema-numbers"></a>Schéma čísla  
 Číslo schématu, která je přiřazená k třídě při `IMPLEMENT_SERIAL` metody třídy je došlo, je "verze" implementaci třídy. Schéma označuje implementaci třídy, se počet, kolikrát daný objekt byl proveden trvalé (obvykle označuje jako verze objektu).  
  
 Pokud máte v úmyslu Údržba několika různými implementacemi stejné třídy v průběhu času, zvyšování schéma, jak můžete zkontrolovat, jestli vaše objekt `Serialize` implementace metod budete moci napsat kód, který může načíst objekty uložené pomocí starší verze implementace.  
  
 `CArchive::ReadObject` Vyvolá metoda výjimku [CArchiveException](../mfc/reference/carchiveexception-class.md) když zjistí schématu číslo trvalého úložiště, který se liší od schématu počet popis třídy v paměti. Není snadno obnovit z této výjimky.  
  
 Můžete použít `VERSIONABLE_SCHEMA` v kombinaci s (bitové `OR`) vaší verze schématu zachovat vyvolání výjimky. Pomocí `VERSIONABLE_SCHEMA`, kódu moci provést vhodnou akci jeho `Serialize` kontrolou návratovou hodnotou z funkce [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).  
  
## <a name="calling-serialize-directly"></a>Volání serializovat přímo  
 V mnoha případech nároky na schéma archivu obecné objekt `WriteObject` a `ReadObject` není nutné. To je běžné serializace dat do [CDocument](../mfc/reference/cdocument-class.md). V takovém případě `Serialize` metodu `CDocument` je volat přímo, ne při operátorů extrakce nebo insert. Obsah dokumentu zase použít obecnější archivu schématu objektu.  
  
 Volání metody `Serialize` přímo má následující výhody a nevýhody:  
  
-   Žádné další bajtů se přidají do archivu před nebo po je objekt serializován. To nejen uložených dat je menší, ale umožňuje implementace `Serialize` rutiny, které může zpracovat všechny formáty souborů.  
  
-   MFC je přizpůsobená proto `WriteObject` a `ReadObject` implementace a související kolekcí nebudou propojené do vaší aplikace, pokud potřebujete další obecné schéma archivu objekt pro některé jinému účelu.  
  
-   Váš kód nebude muset obnovit z původního čísla schématu. Díky tomu kódu serializace dokumentu zodpovědná za kódování schématu čísla, čísla verze souboru formátu nebo jakoukoli identifikace čísla použít na začátku datové soubory.  
  
-   Libovolný objekt, který je serializovat s příznakem přímé volání `Serialize` nesmí používat `CArchive::GetObjectSchema` nebo musí popisovač návratová hodnota -1 (UINT) znamenající, že byla verze neznámé.  
  
 Protože `Serialize` je volána přímo na dokument, není možné obvykle pro dílčí objekty dokumentu pro archivaci odkazy na jejich nadřazené dokumentu. Tyto objekty musí být poskytnut ukazatel k jejich dokument kontejneru explicitně nebo je nutné použít [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkce pro mapování `CDocument` ukazatel na PID předtím, než jsou archivovány tyto pozadí ukazatele.  
  
 Jak již bylo uvedeno dříve, měli byste kódování verze a třídy informací, sami při volání `Serialize` přímo, což umožňuje později změnit formát současně se zachovává zpětnou kompatibilitu s starší soubory. `CArchive::SerializeClass` Funkce se dá volat explicitně před přímo serializace objektu nebo před voláním základní třídy.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

