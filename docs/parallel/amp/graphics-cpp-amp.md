---
title: Grafické prvky (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 6e21c5af094ce90c8e4365ed4263198422ad1905
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449865"
---
# <a name="graphics-c-amp"></a>Grafické prvky (C++ AMP)

C++ AMP obsahuje několik rozhraní API v [Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) obor názvů, který můžete použít pro přístup k podpoře textur na GPU. Jsou uvedeny některé obvyklé scénáře:

- Můžete použít [textury](../../parallel/amp/reference/texture-class.md) třídy jako datový zásobník pro výpočet a využití *prostorová lokalita* mezipaměti textur a rozložení hardwarové GPU. Prostorová lokalita je vlastnost datových prvků, které jsou fyzicky blízko u sebe navzájem.

- Modul runtime poskytuje efektivní spolupráci s nevýpočetními shadery. Pixel, vrchol, teselace a shadery trupu často spotřebovávají nebo vytvářejí textury, které můžete použít v rámci výpočtů C++ AMP.

- Grafické rozhraní API v jazyce C++ AMP poskytují alternativní způsoby přístupu k zabaleným vyrovnávacím pamětem Sub-Word. Textury, které mají formáty představující *texely* (prvky textur), které se skládají z 8bitovými nebo 16bitovými skaláry, umožňují přístup k takovémuto zabalenému úložišti.

## <a name="the-norm-and-unorm-types"></a>Typy norm a unorm

`norm` a `unorm` typy jsou Skalární typy, které omezují rozsah **float** hodnoty, to se označuje jako *upnutí*. Tyto typy lze explicitně zkonstruovat z jiných skalárních typů. Při přetypování je hodnota nejdříve přetypována na **float** a následně upnutá k příslušné oblasti, kterou může norm [-1.0, 1.0] nebo unorm [0.0, 1.0]. Přetypování z +/-nekonečno vrátí +/-1. Přetypování z NaN není definováno. Metoda norm může implicitně vytvořený z unorm a nedochází ke ztrátě dat. Operátor implicitního převodu na float je definován na těchto typech. Binární operátory jsou definovány mezi těmito typy a jinými předdefinovanými skalárními typy, jako **float** a **int**: +, -, \*, /, ==,! =, >, \<, > =, < =. Operátory přiřazení sloučení jsou také podporovány: +=,-=, \*=, / =. Operátor unární negace (-) je definován pro typy norm.

## <a name="short-vector-library"></a>Knihovna krátkých vektorů

Krátká vektorová knihovna poskytuje některé funkce [typ vektoru](https://go.microsoft.com/fwlink/p/?linkid=248500) , který je definován v HLSL a obvykle se používá k definování texelů. Krátký vektor je datová struktura, která obsahuje jednu až čtyři hodnoty stejného typu. Podporované typy jsou **double**, **float**, **int**, `norm`, `uint`, a `unorm`. Názvy typů jsou uvedeny v následující tabulce. Pro každý typ existuje také odpovídající **typedef** , který neobsahuje v názvu podtržítko. Typy obsahující podtržítka jsou [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md). Typy, které nemají podtržítka jsou v [Concurrency::Graphics:: Direct3D – Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) tak, aby zřetelné oddělení od podobně pojmenovaných základních typů jako **__int8** a **__int16**.

||Délka 2|Délka 3|Délka 4|
|-|--------------|--------------|--------------|
|double|double_2 –<br /><br /> double2|double_3 –<br /><br /> double3|double_4 –<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4 –<br /><br /> FLOAT4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2 –<br /><br /> norm2|norm_3 –<br /><br /> norm3|norm_4 –<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2 –<br /><br /> unorm2|unorm_3 –<br /><br /> unorm3|unorm_4 –<br /><br /> unorm4|

### <a name="operators"></a>Operátory

Pokud mezi dvěma vektory definován operátor, pak je také definován mezi krátkým vektorem a skalární. Navíc jeden z nich musí být splněné:

- Typ skaláru musí být stejný jako typ prvku krátkého vektoru.

- Typ skaláru lze implicitně převést na typ prvku vektoru pomocí pouze jednoho uživatelem definovaného převodu.

Operace se provádí s ohledem na komponentu mezi každou součástí krátkého vektoru a skaláru. Zde jsou platné operátory:

|Typ operátoru|Platné typy|
|-------------------|-----------------|
|Binární operátory|Platné pro všechny typy: +, -, \*, /,<br /><br /> Platné pro všechny celočíselné typy: %, ^, &#124;&, <\<, >><br /><br /> Dva vektory musí mít stejnou velikost a výsledkem je vektor stejné velikosti.|
|Relační operátory|Platné pro všechny typy: == a! =|
|Složený operátor přiřazení|Platné pro všechny typy: +=,-=, \*=, / =<br /><br /> Platné pro všechny celočíselné typy: % =, ^ =, &#124;= & =, <\<=, >> =|
|Operátory přírůstku a snížení|Platné pro všechny typy: ++,--<br /><br /> Předpona i přípona jsou platné.|
|Bitový operátor NOT (~)|Platí pro všechny celočíselné typy.|
|Unární operátor - – operátor|Platné pro všechny typy s výjimkou `unorm` a `uint`.|

### <a name="swizzling-expressions"></a>Výrazy swizzling

Knihovna krátkých vektorů podporuje `vector_type.identifier` konstrukci přístupového objektu pro přístup ke komponentám krátkého vektoru. `identifier`, Což se označuje jako *výraz swizzling*, určuje součásti vektoru. Výraz může být l hodnotou nebo r-hodnotou. Jednotlivé znaky v identifikátoru mohou být: x, y, z a w; nebo r, g, b a. "x" a "r" znamenají nultou komponentu, "y" a "g" znamenají první komponentu a tak dále. (Všimněte si, že "x" a "r" nelze použít ve stejném identifikátoru.) Proto "rgba" a "xyzw" vrací stejný výsledek. Jednoduchým součástem, jako je například "x" a "y", jsou skalární hodnotové typy. Ke složeným součástem jsou typy krátkého vektoru. Například, pokud vytvoříte `int_4` vektor, který se jmenuje `fourInts` a hodnotami 2, 4, 6 a 8, pak `fourInts.y` vrátí celé číslo 4 a `fourInts.rg` vrátí `int_2` objekt, který obsahuje hodnoty 2 a 4.

## <a name="texture-classes"></a>Třídy textur

Mnoho grafických karet využívá hardware a, které jsou optimalizovány pro načtení pixelů a texelů a pro vykreslení obrazů a textur. [Textury\<T, N >](../../parallel/amp/reference/texture-class.md) třídu, která je třídou kontejneru pro objekty texelu, zpřístupňuje funkce textury tyto GPU. Texel může být:

- **Int**, `uint`, **float**, **double**, `norm`, nebo `unorm` skalární.

- Krátký vektor, který má dvě nebo čtyři součásti. Jedinou výjimkou je `double_4`, což není povoleno.

`texture` Objekt může mít řád 1, 2 nebo 3. `texture` Objektu můžete zachycen pouze odkazem v lambda výrazu volání `parallel_for_each`. Textura je uložena v GPU jako objekty textur rozhraní Direct3D. Další informace o texturách a texelech v Direct3D naleznete v tématu [Úvod do textur v Direct3D 11](https://go.microsoft.com/fwlink/p/?linkid=248502).

Typ texelu, který používáte, může být jeden z mnoha formátů textur, které se používají v programování grafiky. Například formát RGBA může používat 32 bitů s 8 bity pro R, G, B a skalární prvky. Hardware textury grafické karty může přistupovat k jednotlivým prvkům založeným na formátu. Například může hardware textury Pokud používáte formát RGBA, extrahovat každý 8bitový prvek do 32bitové podoby. V jazyce C++ AMP můžete nastavit bity na skalární prvek texelu tak, aby může automaticky přistupovat k jednotlivým skalárním prvkům v kódu bez použití bitového řazení.

### <a name="instantiating-texture-objects"></a>Vytváření instancí objektů textury

Je možné deklarovat objekt textury bez inicializace. Následující příklad kódu deklaruje několik objektů textury.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

Můžete také použít konstruktor deklarovat a inicializovat `texture` objektu. Následující příklad kódu vytvoří instanci `texture` objekt z vektoru objektu `float_4` objekty. Bity na skalární prvek je nastavena na výchozí hodnotu. Nelze použít tento konstruktor s `norm`, `unorm`, nebo krátké vektory `norm` a `unorm`, protože nemají výchozí počet bitů na skalární prvek.

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

Můžete také deklarovat a inicializovat `texture` objektu pomocí přetížení konstruktoru, který bere ukazatel na zdroj dat, velikost dat v bajtech a bity na skalární prvek.

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

Textury v těchto příkladech jsou vytvořeny ve výchozím zobrazení výchozího akcelerátoru. Můžete použít další přetížení konstruktoru, pokud chcete zadat `accelerator_view` objektu. Nelze vytvořit objekt textury na akcelerátoru procesoru.

Existují omezení velikosti jednotlivých rozměrů `texture` objektu, jak je znázorněno v následující tabulce. Pokud překročíte limity, je vygenerována chyba za běhu.

|Textura|Omezení velikosti na dimenzi|
|-------------|---------------------|
|Textura\<T, 1 >|16384|
|texture\<T,2>|16384|
|texture\<T,3>|2048|

### <a name="reading-from-texture-objects"></a>Čtení z objektů textury

Můžete číst z `texture` s použitím [texture::operator\[\]](reference/texture-class.md#operator_at), [texture:: operator() – operátor](reference/texture-class.md#operator_call), nebo [Texture::Get – metoda](reference/texture-class.md#get). Dva operátory vrací hodnotu, ne odkaz. Proto nelze zapisovat do `texture` s použitím `texture::operator\[\]`.

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

Následující příklad kódu ukazuje způsob uložení kanálů textury v krátkém vektoru a pak přístup k jednotlivým skalárním prvkům jako vlastnosti krátkého vektoru.

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

V následující tabulce jsou uvedeny platné bity na kanál pro každý typ vektoru řazení.

|Datový typ textury|Platné bity na skalární prvek|
|-----------------------|-----------------------------------|
|int, int_2 –, int_4 –<br /><br /> uint, uint_2 –, uint_4 –|8, 16, 32|
|int_3 – uint_3 –|32|
|float, float_2 –, float_4|16, 32|
|float_3|32|
|double_2 – Double|64|
|Norm a norm_2 –, norm_4 –<br /><br /> unorm, unorm_2 –, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>Zapisování do objektů textury

Použití [texture::set](reference/texture-class.md#set) metody zapsat do `texture` objekty. Objekt textury může být jen pro čtení nebo pro čtení a zápisu. Pro objekt textury na čtení a zápis musí být splněny následující podmínky:

- T má pouze jednu skalární součást. (Krátké vektory nejsou povoleny.)

- T není **double**, `norm`, nebo `unorm`.

- `texture::bits_per_scalar_element` Vlastnost je 32.

Pokud nejsou všechny tři splněny, pak bude `texture` objekt je jen pro čtení. První dvě podmínky jsou kontrolovány během kompilace. Pokud máte kód, který se pokouší o zápis, je vygenerována chyba kompilace `readonly` objektu textury. Podmínka pro `texture::bits_per_scalar_element` je zjištěna v době běhu a modul runtime generuje [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) výjimku, pokud se pokusíte napsat jen pro čtení `texture` objektu.

Následující příklad kódu zapíše hodnoty do objektu textury.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>Kopírování objektů textury

Můžete kopírovat mezi objekty textury s použitím [kopírování](reference/concurrency-namespace-functions-amp.md#copy) funkce nebo [copy_async –](reference/concurrency-namespace-functions-amp.md#copy_async) fungovat, jak je znázorněno v následujícím příkladu kódu.

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

Můžete také zkopírovat z jedné textury do jiné pomocí [texture::copy_to](reference/texture-class.md#copy_to) metody. Obě textury mohou být na různých accelerator_views. Při kopírování do `writeonly_texture_view` objektu, jsou data zkopírována do základního `texture` objektu. Bity na skalární prvek a rozsah musí být stejná na zdrojových a cílových `texture` objekty. Pokud tyto požadavky nejsou splněny, modul runtime vyvolá výjimku.

## <a name="texture-view-classes"></a>Třídy zobrazení textur

C++++ AMP představuje [texture_view – třída](../../parallel/amp/reference/texture-view-class.md) v sadě Visual Studio 2013. Zobrazení textury podporují stejné typy a řazení texel jako [texture – třída](../../parallel/amp/reference/texture-class.md), ale na rozdíl od textur poskytují přístup k dalším funkcím hardwaru například vzorkování textury a mipmapy. Zobrazení textury podporují přístup jen pro čtení, pouze pro zápis a čtení i zápis v podkladových datech textury.

- Přístup jen pro čtení je poskytován `texture_view<const T, N>` textury specializace šablony, které podporují prvky, které mají 1, 2 nebo 4 komponenty, vzorkování a dynamický přístup k rozsahu úrovní mipmap, které jsou určeny při vytváření instance zobrazení.

- Přístup jen pro zápis je poskytován základě nespecializované šablony třídy `texture_view<T, N>`, která podporuje prvky, které mají 2 nebo 4 komponenty a mají přístup k jedné úrovni mipmap určené při vytváření instance zobrazení. Vzorkování není podporováno.

- Přístup pro čtení a zápis je poskytován šablonu na základě nespecializované třídy `texture_view<T, N>`, která, stejně jako textury, podporuje prvky, které mají pouze jednu komponentu, zobrazení může přistupovat k jedné úrovni mipmap, která je určena, když je vytvořena instance. Vzorkování není podporováno.

Zobrazení textury jsou podobná zobrazením polí, ale neposkytují funkci správy a pohybu dat, která [array_view – třída](../../parallel/amp/reference/array-view-class.md) nabízí v porovnání [array – třída](../../parallel/amp/reference/array-class.md). A `texture_view` je přístupný pouze na akcelerátoru zobrazení, ve které se nachází v podkladových datech textury.

### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view – nepoužívané

Pro sadu Visual Studio 2013 C++ AMP přináší lepší podporu funkcí hardwaru pro textury jako je odběr vzorků a Mipmap, které nemusí být podporovány [writeonly_texture_view – třída](../../parallel/amp/reference/writeonly-texture-view-class.md). Nově zavedená `texture_view` třída podporuje nadmnožinu funkcí v `writeonly_texture_view`; v důsledku toho `writeonly_texture_view` je zastaralý.

Doporučujeme – alespoň pro nový kód –, který používáte `texture_view` pro přístup k funkcím, které byly dříve poskytovány pomocí `writeonly_texture_view`. Porovnejte následující dva příklady, které se zápis do objektu textury, která má dvě součásti (int_2). Všimněte si, že v obou případech platí, zobrazení `wo_tv4`, musí být zachyceno hodnotou ve výrazu lambda. Tady je příklad, který používá novou `texture_view` třídy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

A zde je zastaralá `writeonly_texture_view` třídy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Jak vidíte, dva příklady jsou téměř identické, pokud všechny prováděné činnosti provádějí zapisuje do na úrovni primární mipmapy. Pokud jste použili `writeonly_texture_view` v existujícím kódu a neplánujete vylepšit, že kód, není nutné ho změnit. Nicméně pokud uvažujete o převedení tohoto kódu vpřed, doporučujeme přepsat ho pomocí `texture_view` protože vylepšení v něm podporují nové funkce textury hardwaru. Přečtěte si další informace o těchto nových funkcí.

Další informace o zavržení `writeonly_texture_view`, naleznete v tématu [přehled návrhu zobrazení textury v C++ AMP](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) na paralelní programování v blogu nativního kódu.

### <a name="instantiating-texture-view-objects"></a>Vytváření instancí objektů zobrazení textury

Deklarace `texture_view` je podobná deklaraci `array_view` , který je přidružený **pole**. Následující příklad kódu deklaruje několik `texture` objekty a `texture_view` objekty, které jsou s nimi spojeny.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

Všimněte si, jak zobrazení textury jejíž typ elementu je nekonstantní a má jednu součást je pro čtení i zápis, ale zobrazení textury, jejíž typ elementu je nekonstantní, ale má více než jednu součást jsou jen pro zápis. Zobrazení textur typů prvků const jsou vždy jen pro čtení, ale pokud je typ prvku nekonstantní, pak počet součástí v prvku určuje, zda je pro čtení i zápis (1 komponenta) nebo pouze pro zápis (více komponent).

Typ elementu `texture_view`– jeho const-ness a také počet komponent, které má, také hraje roli při určování, zda zobrazení podporuje vzorkování textury a jak je přístupný úrovní mipmap:

|Type|Komponenty|Číst|Write|Vzorkování|Přístup Mipmap|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N >|1, 2, 4|Ano|Ne (1)|Ano|Ano, indexovatelné. Rozsah je určena při instanci.|
|Texture_view\<T, N>|1<br /><br /> 2, 4|Ano<br /><br /> Ne (2)|Ano<br /><br /> Ano|Ne (1)<br /><br /> Ne (1)|Ano, jedna úroveň. Úroveň je určena při instanci.<br /><br /> Ano, jedna úroveň. Úroveň je určena při instanci.|

Z této tabulky uvidíte, že zobrazení textur jen pro čtení plně podporují nové možnosti výměnou nemůže zapisovat do zobrazení. Zapisovatelné zobrazení textur jsou omezeny v tom, že jsou přístup pouze k jedné úrovni mipmap. Zobrazení textur pro čtení a zápis jsou ještě více specializované než ty výhradně zapisovatelné, protože přidávají požadavek, aby typ prvku zobrazení textury měl pouze jednu komponentu. Všimněte si, že vzorkování není podporováno pro zobrazení textury s možností zápisu, protože se jedná operaci čtení.

### <a name="reading-from-texture-view-objects"></a>Čtení z objektů zobrazení textury

Čtení nevzorkovaných textury dat prostřednictvím zobrazení textury je stejné jako čtení z textury, s tím rozdílem, že textury jsou zachycovány na základě odkazu, zatímco zobrazení textury jsou zachyceny hodnotou. Následující dva příklady ukazují; Nejprve je potřeba pomocí `texture` pouze:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

A zde je stejný příklad, s tím rozdílem, že nyní používá `texture_view` třídy:

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

Texture – zobrazení, jehož prvky jsou založeny na typech s plovoucí desetinnou čárkou, například float, float_2 – nebo float_4 – lze také číst pomocí odběru vzorků textury výhod hardwarové podpory pro různé režimy filtrování a adresování. C++ AMP podporuje dva režimy filtrování, které jsou nejčastější ve výpočetních scénářích – bod filtrování (Nejbližší soused) a lineární filtrování (vážený průměr) – a čtyři režimy adresování – zabalené, zrcadlené, omezen a ohraničení. Další informace o režimech adresování naleznete v tématu [address_mode – výčet](reference/concurrency-graphics-namespace-enums.md#address_mode).

Kromě režimů, které přímo podporují C++ AMP může přístup ostatním režimům filtrování a režimům adresování základní platformy pomocí rozhraní API zprostředkovatele pro osvojení vzorkovače textury, který byl vytvořen přímo pomocí rozhraní API platformy. Direct3D například podporuje jiné režimy filtrování, například anizotropní filtrování a můžete použít jiný režim adresování pro každou dimenzi textury. Můžete vytvořit vzorkovač textury, jehož souřadnice jsou zabaleny svisle, zrcadleny vodorovně a vzorkovány pomocí anizotropního filtrování pomocí rozhraní API Direct3D a pak ho využít ve svém kódu C++ AMP pomocí `make_sampler` vzájemné spolupráce rozhraní API. Další informace najdete v části [vzorkování textur v c ++ AMP](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) na paralelní programování v blogu nativního kódu.

Zobrazení textury také podporují čtení Mipmap. Zobrazení textur jen pro čtení (těch, které mají konstantní typ prvku) nabízí největší flexibilitu, protože rozsah úrovně mip, která je určena při instanci, lze dynamicky vzorkovat, a protože jsou podporovány prvky, které mají 1, 2 nebo 4 komponenty. Zobrazení textury pro čtení i zápis, která mají prvky, které mají jednu komponentu, také podporují mipmapy, ale pouze pro úroveň, která je určena při instanci. Další informace najdete v tématu [textury s Mipmaps](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) na paralelní programování v blogu nativního kódu.

### <a name="writing-to-texture-view-objects"></a>Zapisování do objektů zobrazení textury

Použití [texture_view::Get – metoda](reference/texture-view-class.md#get) k zápisu do základní `texture` prostřednictvím `texture_view` objektu. Zobrazení textury může být jen pro čtení, čtení a zápis nebo jen pro zápis. Pro zobrazení textury jako zapisovatelné musí mít typ elementu, který je nekonstantní; pro zobrazení textury na čtení a zápis musí jeho typ elementu také mít pouze jednu komponentu. V opačném případě je zobrazení textury jen pro čtení. Je možné jenom přístup k jedné úrovni mipmap textury najednou prostřednictvím zobrazení textury a úroveň je určena při vytváření instance zobrazení.

Tento příklad ukazuje, jak zapisovat druhé nejvíce podrobné úrovně mipmap textury, která má 4 úrovně mipmap. Nejpodrobnější úroveň mipmap je úroveň 0.

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>Interoperabilita

Runtime C++ AMP podporuje interoperabilitu mezi `texture<T,1>` a [ID3D11Texture1D rozhraním](https://go.microsoft.com/fwlink/p/?linkId=248503), mezi `texture<T,2>` a [ID3D11Texture2D rozhraním](https://go.microsoft.com/fwlink/p/?linkId=255317)a mezi `texture<T,3>`a [ID3D11Texture3D rozhraním](https://go.microsoft.com/fwlink/p/?linkId=255377). [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) přijímá metodu `texture` objekt a vrátí `IUnknown` rozhraní. [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) přijímá metodu `IUnknown` rozhraní a `accelerator_view` objekt a vrátí `texture` objektu.

## <a name="see-also"></a>Viz také:

[double_2 – třída](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3 – třída](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4 – třída](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2 – třída](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3 – třída](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4 – třída](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2 – třída](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3 – třída](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4 – třída](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2 – třída](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3 – třída](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4 – třída](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector – struktura](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits – struktura](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2 – třída](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3 – třída](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4 – třída](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2 – třída](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3 – třída](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4 – třída](../../parallel/amp/reference/unorm-4-class.md)
