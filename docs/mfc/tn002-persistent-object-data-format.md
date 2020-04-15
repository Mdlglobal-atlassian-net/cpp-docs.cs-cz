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
ms.openlocfilehash: f65a7b7afcf6bd832c9c23560bb29374038fae1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370446"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: Formát dat trvalých objektů

Tato poznámka popisuje rutiny knihovny MFC, které podporují trvalé objekty jazyka C++ a formát dat objektu při uložení v souboru. To platí pouze pro třídy s [makry DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL.](../mfc/reference/run-time-object-model-services.md#implement_serial)

## <a name="the-problem"></a>Problém

Implementace knihovny MFC pro trvalá data ukládá data pro mnoho objektů v jedné souvislé části souboru. `Serialize` Metoda objektu převádí data objektu do kompaktního binárního formátu.

Implementace zaručuje, že všechna data jsou uložena ve stejném formátu pomocí [CArchive Class](../mfc/reference/carchive-class.md). Používá `CArchive` objekt jako překladač. Tento objekt přetrvává od okamžiku, kdy je vytvořen, dokud nezavoláte [CArchive::Close](../mfc/reference/carchive-class.md#close). Tato metoda může být volána buď explicitně programátorem nebo implicitně destruktorem, když program ukončí obor, který obsahuje `CArchive`.

Tato poznámka popisuje implementaci `CArchive` členů [CArchive::ReadObject](../mfc/reference/carchive-class.md#readobject) a [CArchive::WriteObject](../mfc/reference/carchive-class.md#writeobject). Kód pro tyto funkce najdete v Arcobj.cpp a `CArchive` hlavní implementaci v Arccore.cpp. Uživatelský kód `ReadObject` nevolá `WriteObject` a přímo. Místo toho tyto objekty jsou používány operátory vkládání a extrakce specifické pro daný typ třídy, které jsou generovány automaticky DECLARE_SERIAL a IMPLEMENT_SERIAL makra. Následující kód ukazuje, jak `WriteObject` a `ReadObject` jsou implicitně volány:

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

Metoda `CArchive::WriteObject` zapisuje data záhlaví, která se používá k rekonstrukci objektu. Tato data se skládá ze dvou částí: typ objektu a stav objektu. Tato metoda je také zodpovědná za udržování identity objektu, který je zapsán, takže je uložena pouze jedna kopie, bez ohledu na počet ukazatelů na tento objekt (včetně kruhových ukazatelů).

Ukládání (vkládání) a obnovení (extrahování) objektů závisí na několika "konstantách manifestu". Jedná se o hodnoty, které jsou uloženy v binárním formátu a poskytují důležité informace do archivu (všimněte si, že předpona "w" označuje 16bitová množství):

|Značka|Popis|
|---------|-----------------|
|wNullTag|Používá se pro ukazatele objektu NULL (0).|
|wNewClassTag|Označuje popis třídy, která následuje, je v tomto kontextu archivu nová (-1).|
|wOldClassTag|Označuje, že třída čteného objektu byla viděna v tomto kontextu (0x8000).|

Při ukládání objektů archiv udržuje [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) *(m_pStoreMap),* což je mapování z uloženého objektu na 32bitový trvalý identifikátor (PID). PID je přiřazen ke každému jedinečnému objektu a každému jedinečnému názvu třídy, který je uložen v kontextu archivu. Tyto PID jsou rozdávány postupně od 1. Tyto PID nemají žádný význam mimo rozsah archivu a zejména nesmí být zaměňovány s čísly záznamů nebo jinými položkami totožnosti.

Ve `CArchive` třídě jsou PIDs 32bitové, ale jsou zapsány jako 16bitové, pokud nejsou větší než 0x7FFE. Velké PID jsou zapsány jako 0x7FFF následovaný 32bitové PID. Tím je zachována kompatibilita s projekty, které byly vytvořeny v dřívějších verzích.

Při požadavku na uložení objektu do archivu (obvykle pomocí operátoru global insertion) se provádí kontrola ukazatele NULL [CObject.](../mfc/reference/cobject-class.md) Pokud je ukazatel NULL, *wNullTag* je vložen do datového proudu archivu.

Pokud ukazatel není NULL a může být serializován `DECLARE_SERIAL` (třída je třída), kód zkontroluje *m_pStoreMap,* zda byl objekt již uložen. Pokud ano, kód vloží 32bitový PID přidružený k tomuto objektu do datového proudu archivu.

Pokud objekt nebyl uložen dříve, existují dvě možnosti, aby zvážila: buď objekt a přesný typ (to znamená, třída) objektu jsou nové tohoto kontextu archivu, nebo objekt je přesného typu již vidět. Chcete-li zjistit, zda byl typ viděn, kód dotazuje *m_pStoreMap* pro `CRuntimeClass` [cRuntimeClass](../mfc/reference/cruntimeclass-structure.md) objekt, který odpovídá objektu přidruženému k uloženému objektu. Pokud je shoda, `WriteObject` vloží značku, která je `OR` bit moudrý *wOldClassTag* a tento index. Pokud `CRuntimeClass` je nový kontext tohoto `WriteObject` archivu, přiřadí nové PID této třídě a vloží ji do archivu, před cvorákem *wNewClassTag.*

Deskriptor pro tuto třídu je pak vložen `CRuntimeClass::Store` do archivu pomocí metody. `CRuntimeClass::Store`vloží číslo schématu třídy (viz níže) a název textu ASCII třídy. Všimněte si, že použití textového názvu ASCII nezaručuje jedinečnost archivu napříč aplikacemi. Proto byste měli označit datové soubory, abyste zabránili poškození. Po vložení informací o třídě archiv vloží objekt do *m_pStoreMap* a `Serialize` pak zavolá metodu pro vložení dat specifických pro třídu. Umístění objektu *m_pStoreMap* do m_pStoreMap `Serialize` před voláním zabrání uložení více kopií objektu do úložiště.

Při návratu k počátečnímu volajícímu (obvykle kořenové síti objektů) musíte zavolat [CArchive::Close](../mfc/reference/carchive-class.md#close). Pokud máte v plánu provádět další operace `CArchive` [CFile,](../mfc/reference/cfile-class.md)musíte volat metodu [Flush,](../mfc/reference/carchive-class.md#flush) abyste zabránili poškození archivu.

> [!NOTE]
> Tato implementace ukládá pevný limit indexů 0x3FFFFFFE na kontext archivu. Toto číslo představuje maximální počet jedinečných objektů a tříd, které lze uložit do jednoho archivu, ale jeden soubor disku může mít neomezený počet kontextů archivu.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>Načítání objektů z úložiště (CArchive::ReadObject)

Loading (extrahování) `CArchive::ReadObject` objekty používá metodu a je konverzovat `WriteObject`. Stejně `WriteObject` `ReadObject` jako u , není volána přímo uživatelským kódem; uživatelský kód by měl volat operátor `ReadObject` extrakce `CRuntimeClass`bezpečného typu, který volá s očekávaným . Tím se zajistí integrita typu operace extrakce.

Vzhledem `WriteObject` k tomu, že implementace přiřazena zvýšení PID, počínaje 1 `ReadObject` (0 je předdefinována jako objekt NULL), implementace můžete použít pole k udržení stavu kontextu archivu. Při čtení PID z úložiště, pokud PID je větší než *m_pLoadArray*aktuální `ReadObject` horní mez m_pLoadArray , ví, že nový objekt (nebo popis třídy) následuje.

## <a name="schema-numbers"></a>Čísla schématu

Číslo schématu, které je přiřazeno třídě, `IMPLEMENT_SERIAL` když je zjištěna metoda třídy, je "verze" implementace třídy. Schéma odkazuje na implementaci třídy, nikoli na počet, kolikrát byl daný objekt proveden trvalý (obvykle označovaný jako verze objektu).

Pokud máte v úmyslu udržovat několik různých implementací stejné třídy v průběhu času, zvýšení `Serialize` schématu při revizi implementace metody objektu vám umožní psát kód, který může načíst objekty uložené pomocí staršíverze implementace.

Metoda `CArchive::ReadObject` vyvolá [CArchiveException,](../mfc/reference/carchiveexception-class.md) když narazí na číslo schématu v trvalém úložišti, které se liší od čísla schématu popisu třídy v paměti. Není snadné se zotavit z této výjimky.

Můžete použít `VERSIONABLE_SCHEMA` v kombinaci s (bitové **NEBO)** verze schématu zachovat tuto výjimku z vyvolání. Pomocí `VERSIONABLE_SCHEMA`kódu můžete provést příslušnou akci `Serialize` ve své funkci kontrolou vrácené hodnoty z [CArchive::GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema).

## <a name="calling-serialize-directly"></a>Volání Serializovat přímo

V mnoha případech režie obecného schématu archivu `WriteObject` objektů a `ReadObject` není nutné. Toto je běžný případ serializace dat do [CDocument](../mfc/reference/cdocument-class.md). V tomto případě `Serialize` je `CDocument` metoda volána přímo, nikoli s operátory extrakce nebo vložení. Obsah dokumentu může zase použít obecnější schéma archivace objektů.

Přímé `Serialize` volání má následující výhody a nevýhody:

- Žádné další bajty jsou přidány do archivu před nebo po objektu serializovat. To nejen zmenší uložená data, ale `Serialize` umožňuje implementovat rutiny, které mohou zpracovávat všechny formáty souborů.

- Knihovna MFC je `WriteObject` vyladěna tak, aby implementace a `ReadObject` implementace a související kolekce nebudou propojeny do vaší aplikace, pokud nepotřebujete obecnější schéma archivace objektů pro jiný účel.

- Váš kód se nemusí zotavit ze starých čísel schématu. Díky tomu je kód serializace dokumentu zodpovědný za kódování čísel schématu, čísel verzí ve formátu souboru nebo identifikačních čísel, která používáte na začátku datových souborů.

- Jakýkoli objekt, který je serializován `Serialize` s `CArchive::GetObjectSchema` přímým voláním, nesmí používat nebo musí zpracovávat vrácenou hodnotu (UINT)-1 označující, že verze byla neznámá.

Protože `Serialize` je volána přímo v dokumentu, není obvykle možné, aby dílčí objekty dokumentu archivovaly odkazy na nadřazený dokument. Tyto objekty musí mít ukazatel na jejich dokumentu kontejneru explicitně nebo je `CDocument` nutné použít [CArchive::MapObject](../mfc/reference/carchive-class.md#mapobject) funkce mapovat ukazatel na PID před tyto ukazatele zpět jsou archivovány.

Jak již bylo uvedeno dříve, měli byste zakódovat informace o verzi a třídě sami, když voláte `Serialize` přímo, což vám umožní změnit formát později při zachování zpětné kompatibility se staršími soubory. Funkce `CArchive::SerializeClass` může být volána explicitně před přímoserializací objektu nebo před voláním základní třídy.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
