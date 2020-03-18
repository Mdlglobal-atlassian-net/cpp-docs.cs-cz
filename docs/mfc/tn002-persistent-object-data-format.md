---
title: 'TN002: Formát dat trvalých objektů'
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: 1880d5d43055966dea8ab16dc4f26bd4e4602ec5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447137"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formát dat trvalých objektů

Tato poznámka popisuje rutiny knihovny MFC, které podporují C++ trvalé objekty a formát dat objektů, když jsou uloženy v souboru. To platí pouze pro třídy, které mají makra [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) .

## <a name="the-problem"></a>Problém

Implementace MFC pro trvalá data ukládá data pro mnoho objektů v jedné sousední části souboru. Metoda `Serialize` objektu překládá data objektu do kompaktního binárního formátu.

Implementace zaručuje, že všechna data budou uložena ve stejném formátu pomocí [třídy CArchive](../mfc/reference/carchive-class.md). Jako překladatel používá objekt `CArchive`. Tento objekt bude v době, kdy bude vytvořen, trvat, dokud nebudete volat [CArchive:: Close](../mfc/reference/carchive-class.md#close). Tuto metodu lze volat buď explicitně programátorem, nebo implicitně destruktorem, když program ukončí rozsah obsahující `CArchive`.

Tato poznámka popisuje implementaci `CArchive` členů [CArchive:: ReadObject](../mfc/reference/carchive-class.md#readobject) a [CArchive:: WriteObject](../mfc/reference/carchive-class.md#writeobject). Kód pro tyto funkce najdete v Arcobj. cpp a hlavní implementaci pro `CArchive` v Arccore. cpp. Uživatelský kód nevolá `ReadObject` a `WriteObject` přímo. Místo toho jsou tyto objekty používány operátory vkládání a extrahování specifických pro třídy, které jsou generovány automaticky pomocí DECLARE_SERIAL a IMPLEMENT_SERIAL maker. Následující kód ukazuje, jak jsou `WriteObject` a `ReadObject` implicitně volány:

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

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>Ukládání objektů do úložiště (CArchive:: WriteObject)

Metoda `CArchive::WriteObject` zapisuje data hlaviček, která slouží k rekonstrukci objektu. Tato data se skládají ze dvou částí: typu objektu a stavu objektu. Tato metoda je také odpovědná za udržování identity vypsaného objektu, takže se uloží jenom jedna kopie, bez ohledu na počet ukazatelů na daný objekt (včetně kruhových ukazatelů).

Ukládání (vkládání) a obnovení (extrakce) objektů spoléhá na několik konstant manifestu. Jedná se o hodnoty, které jsou uložené v binárním souboru a poskytují důležité informace archivu (Všimněte si, že předpona "w" označuje 16 bitů množství):

|Značka|Popis|
|---------|-----------------|
|wNullTag|Používá se pro ukazatele objektu s hodnotou NULL (0).|
|wNewClassTag|Označuje popis třídy, který následuje za novým v tomto archivním kontextu (-1).|
|wOldClassTag|Indikuje, že se v tomto kontextu (0x8000) zobrazila třída čteného objektu.|

Při ukládání objektů archiv udržuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*), což je mapování uloženého objektu na 32 trvalý identifikátor (PID). Identifikátor PID je přiřazen každému jedinečnému objektu a každému jedinečnému názvu třídy, který je uložen v kontextu archivu. Tyto PID jsou předány postupně od 1. Tyto PID nemají žádný význam mimo rozsah archivu a zejména se Nezaměňujte s čísly záznamů nebo jinými položkami identity.

Ve třídě `CArchive` jsou PID 32-bit, ale jsou zapsány jako 16bitové, pokud nejsou větší než 0x7FFE. Velké PID se zapisují jako 0x7FFF, po kterém následují 32-bit PID. Tím se udržuje kompatibilita s projekty, které byly vytvořeny v dřívějších verzích.

Pokud je učiněn požadavek na uložení objektu do archivu (obvykle pomocí operátoru globálního vložení), je provedena kontroly pro nulový ukazatel [CObject](../mfc/reference/cobject-class.md) . Pokud je ukazatel NULL, je *wNullTag* vložen do archivního datového proudu.

Pokud ukazatel není NULL a lze jej serializovat (třída je `DECLARE_SERIAL` třídy), kód zkontroluje *m_pStoreMap* a zjistí, zda byl objekt již uložen. Pokud má, kód vloží 32. bit PID přidružený k tomuto objektu do archivního datového proudu.

Pokud objekt nebyl uložen dříve, existují dvě možnosti, které je třeba vzít v úvahu: buď jak objekt, tak přesný typ (tj. třída) objektu jsou v tomto archivním kontextu nové, nebo je objekt typu, který již byl zobrazen přes přesný typ. Aby bylo možné zjistit, zda byl typ zjištěn, kód dotazuje *m_pStoreMap* pro objekt [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) , který odpovídá objektu `CRuntimeClass` přidruženému k uloženému objektu. Pokud existuje shoda, `WriteObject` vloží značku, která je bitově `OR` *wOldClassTag* a index. Pokud je `CRuntimeClass` do tohoto archivního kontextu nový, `WriteObject` přiřadí k této třídě nové PID a vloží je do archivu, před kterým bude hodnota *wNewClassTag* .

Popisovač pro tuto třídu je pak vložen do archivu pomocí metody `CRuntimeClass::Store`. `CRuntimeClass::Store` vloží číslo schématu třídy (viz níže) a textový název ASCII třídy. Všimněte si, že použití textového názvu ASCII nezaručuje jedinečnost archivace napříč aplikacemi. Proto byste měli označit datové soubory a zabránit tak poškození. Po vložení informací o třídě archiv vloží objekt do *m_pStoreMap* a potom zavolá metodu `Serialize` pro vložení dat specifických pro třídu. Umístění objektu do *m_pStoreMap* před voláním `Serialize` zabrání ukládání více kopií objektu do úložiště.

Při návratu na počátečního volajícího (obvykle kořen sítě objektů) musíte zavolat [CArchive:: Close](../mfc/reference/carchive-class.md#close). Pokud máte v úmyslu provádět jiné operace [CFile –](../mfc/reference/cfile-class.md), je nutné [zavolat metodu `CArchive`, aby](../mfc/reference/carchive-class.md#flush) se zabránilo poškození archivu.

> [!NOTE]
>  Tato implementace ukládá pevně stanovený limit 0x3FFFFFFE indexů na archivní kontext. Toto číslo představuje maximální počet jedinečných objektů a tříd, které mohou být uloženy v jednom archivu, ale jeden soubor na disku může mít neomezený počet kontextů archivu.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Načítání objektů z úložiště (CArchive:: ReadObject)

Načítání (extrakce) objektů používá metodu `CArchive::ReadObject` a je `WriteObject`. Stejně jako u `WriteObject``ReadObject` není volána přímo uživatelským kódem; uživatelský kód by měl volat operátor pro extrakci, který je typově bezpečný, který volá `ReadObject` s očekávaným `CRuntimeClass`. To zajišťují integritu typu operace extrakce.

Vzhledem k tomu, že implementace `WriteObject` přiřadila zvýšení PID, počínaje hodnotou 1 (0 je předdefinovaná jako objekt NULL), implementace `ReadObject` může použít pole k údržbě stavu archivního kontextu. Pokud je PID čten ze Storu, pokud je PID větší než aktuální horní mez *m_pLoadArray*, `ReadObject` ví, že následuje nový objekt (nebo popis třídy).

## <a name="schema-numbers"></a>Čísla schémat

Číslo schématu, které je přiřazeno třídě při zjištění metody `IMPLEMENT_SERIAL` třídy, je "verze" implementace třídy. Schéma odkazuje na implementaci třídy, nikoli na počet, kolikrát daný objekt byl vytvořen jako trvalý (obvykle označovaný jako verze objektu).

Pokud máte v úmyslu zachovat několik různých implementací stejné třídy v průběhu času, při změně implementace `Serialize` metody vašeho objektu se vám umožní napsat kód, který může načíst objekty uložené pomocí starších verzí implementace.

Metoda `CArchive::ReadObject` vyvolá výjimku [CArchiveException](../mfc/reference/carchiveexception-class.md) , pokud nalezne číslo schématu v trvalém úložišti, které se liší od čísla schématu popisu třídy v paměti. Z této výjimky není snadné ji obnovovat.

Můžete použít `VERSIONABLE_SCHEMA` v kombinaci s (bitové **nebo**) verze schématu a zabránit tak vyjímka této výjimky. Pomocí `VERSIONABLE_SCHEMA`může váš kód v rámci své `Serialize` funkce provést příslušnou akci kontrolou návratové hodnoty z [CArchive:: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Přímé volání serializace

V mnoha případech není nutné režii `WriteObject` obecné schéma objektů archivu a `ReadObject`. Toto je běžný případ serializace dat do [objektu CDocument](../mfc/reference/cdocument-class.md). V tomto případě je metoda `Serialize` `CDocument` volána přímo, nikoli pomocí operátorů Extract nebo INSERT. Obsah dokumentu může zase použít obecnější schéma archivu objektů.

Přímé volání `Serialize` má následující výhody a nevýhody:

- Do archivu nejsou přidány žádné nadbytečné bajty před nebo po serializaci objektu. Tím se nejen data ukládají menším způsobem, ale umožňuje implementovat rutiny `Serialize`, které mohou zpracovávat libovolné formáty souborů.

- Knihovna MFC je vyladěna, takže implementace `WriteObject` a `ReadObject` a související kolekce nebudou propojeny do vaší aplikace, pokud nepotřebujete obecnější schéma pro archivní objekty pro nějaký jiný účel.

- Váš kód nemusí obnovovat ze starých čísel schémat. Tím se kód serializace dokumentu zodpovídá za kódování čísel schématu, čísel verzí formátu souboru nebo libovolných identifikačních čísel, která používáte na začátku vašich datových souborů.

- Libovolný objekt, který je serializován s přímým voláním `Serialize` nesmí používat `CArchive::GetObjectSchema` nebo musí zpracovat návratovou hodnotu (UINT)-1, která označuje, že verze byla neznámá.

Vzhledem k tomu, že `Serialize` je volána přímo v dokumentu, není obvykle možné podobjektům dokumentu archivovat odkazy na svůj nadřazený dokument. Těmto objektům musí být explicitně udělen ukazatel na jejich dokument kontejneru nebo je nutné použít funkci [CArchive:: MapObject](../mfc/reference/carchive-class.md#mapobject) k mapování `CDocument` ukazatele na PID před archivací těchto koncových bodů.

Jak bylo uvedeno dříve, měli byste kódovat informace o verzi a třídě sami při volání `Serialize` přímo, což vám umožní později změnit formát a zároveň zachovat zpětnou kompatibilitu se staršími soubory. Funkci `CArchive::SerializeClass` lze volat explicitně před přímým serializací objektu nebo před voláním základní třídy.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
