---
title: Grafika (C++ AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: daff070700c37734e6239514d196f02ee1351c00
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="graphics-c-amp"></a>Grafické prvky (C++ AMP)
Obsahuje několik rozhraní API v C++ AMP [Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) obor názvů, který můžete použít pro přístup k podpoře texture na grafickými procesory. Jsou některé běžné scénáře:  
  
-   Můžete použít [texture](../../parallel/amp/reference/texture-class.md) třída jako kontejner dat pro výpočty a zneužití *prostorových polohu* texture mezipaměti a rozložení GPU hardwaru. Prostorové polohu je vlastnost datové prvky, které se fyzicky blízko sebe navzájem.  
  
-   Modul runtime umožňuje efektivní spolupráci s shadery bez výpočtů. Pixelů, vrchol, teselace a trupu shadery často využívat nebo vytvářet textury, které můžete použít v vaší C++ AMP výpočty.  
  
-   Grafické rozhraní API v C++ AMP poskytují alternativní způsoby pro přístup k dílčí aplikace word sbalené vyrovnávací paměti. Textury, které mají formáty, které představují *texels* (texture elementy), se skládají z 8bitové nebo 16bitové skalárních hodnot povolit přístup k úložišti takové zabalená data.  
  
## <a name="the-norm-and-unorm-types"></a>Norm a unorm typy  
 `norm` a `unorm` typy jsou Skalární typy, které omezí rozsah `float` hodnoty, to se označuje jako *upínací*. Tyto typy lze explicitně sestavit od ostatních typů skalární. V přetypování, hodnota nejprve vložena do `float` a pak těsně příslušných oblast, která je povolena norm [-1.0, 1.0] nebo unorm [0,0, 1.0]. Přetypování z +/-infinity vrátí +/-1. Přetypování z NaN není definován. Norm být implicitně konstruovat z unorm a nedochází ke ztrátě dat. Implicitní převod operátorovi float je definována v těchto typů. Binární operátory jsou definované mezi tyto typy a jiné předdefinované Skalární typy, jako `float` a `int`: +, -, *, /, ==,! =, >, \<, > =, < =. Jsou podporovány také složené operátory přiřazení: +=,-=, \*= / =. Operátor unární negace (-) je pro typy norm definované.  
  
## <a name="short-vector-library"></a>Vektor krátké knihovna  
 Krátké knihovna vektoru obsahuje některé funkce [vektoru typ](http://go.microsoft.com/fwlink/p/?linkid=248500) která je definována v HLSL a obvykle se používá k definování texels. Krátký vektor je datová struktura, která obsahuje jeden až čtyři hodnoty stejného typu. Podporované typy jsou `double`, `float`, `int`, `norm`, `uint`, a `unorm`. V následující tabulce jsou uvedeny názvy typů. Pro každý typ je také odpovídající `typedef` podtržítko, nebude mít v názvu. Typy, které mají podtržítka jsou v [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md). Typy, které nemají podtržítka jsou v [Concurrency::Graphics:: Direct3D – Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) tak, aby se jsou oddělena od podobně názvem základní typy, jako `__int8` a `__int16`.  
  
||Délka 2|Délka 3|Délka 4|  
|-|--------------|--------------|--------------|  
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|  
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> FLOAT4|  
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|  
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|  
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|  
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|  
  
### <a name="operators"></a>Operátory  
 Pokud operátor je definována mezi dvěma krátké vektory, pak je také definován mezi krátké vektoru a skalární hodnota. Navíc jeden z nich musí být splněné:  
  
-   Typ skalární hodnota musí být stejný jako typ elementu krátké vektoru.  
  
-   Typ skalárních můžete implicitně převést na typ elementu vektoru pomocí pouze jeden převod definovaný uživatelem.  
  
 Operace probíhá component-wise mezi jednotlivé komponenty krátké vektoru a skalárních. Zde jsou platné operátory:  
  
|Typ – operátor|Platné typy|  
|-------------------|-----------------|  
|Binární operátory|Platná pro všechny typy: +, -, *, /,<br /><br /> Platné typy celého čísla: %, ^, &#124;&, <\<, >><br /><br /> Dva vektory musí mít stejnou velikost a výsledkem je vektor stejnou velikost.|  
|Relační operátory|Platná pro všechny typy: == a! =|  
|Operátor složené přiřazení|Platná pro všechny typy: +=,-=, * = / =<br /><br /> Platné typy celého čísla: % =, ^ =, &#124;= & =, <\<=, >> =|  
|Operátory přírůstku a snížení|Platná pro všechny typy: ++, –<br /><br /> Předpona a operátory jsou platné.|  
|Bitový operátor NOT (~)|Platné na typy celého čísla.|  
|Unární – operátor|Platná pro všechny typy kromě `unorm` a `uint`.|  
  
### <a name="swizzling-expressions"></a>Swizzling výrazy  
 Podporuje krátké knihovna vektoru `vector_type.identifier` přistupujícího objektu konstrukce pro přístup k součástem krátké vektoru. `identifier`, Což se označuje jako *swizzling výraz*, určuje součástí vektoru. Výraz může být hodnotu l nebo r-value. Může být jednotlivé znaky v identifikátoru: x, y, z a w; g, b, nebo r a. "x" a "r" znamená nula tý součásti, "y" a "g" střední první součást a tak dále. (Všimněte si, že "x" a "r" nelze použít ve stejný identifikátor.) Tedy "rgba" a "xyzw" vrátí stejný výsledek. Přístupové objekty jedné součásti jako je například "x" a "y" jsou typy skalární hodnotu. Přístupové objekty více součásti jsou typy krátké vektoru. Například pokud vytvoříte `int_4` vektor, který je s názvem `fourInts` a má hodnoty 2, 4, 6 a 8, pak `fourInts.y` vrátí celé číslo 4 a `fourInts.rg` vrátí `int_2` objekt, který obsahuje hodnoty 2 a 4.  
  
## <a name="texture-classes"></a>Texture – třídy  
 Mnoho grafickými procesory mít hardwaru a mezipaměti, které jsou optimalizovány načíst pixelů a texels a k vykreslení obrázků a textury. [Texture\<T, N >](../../parallel/amp/reference/texture-class.md) třída, která je třídu kontejneru pro objekty texel, zpřístupňuje funkce texture tyto grafickými procesory. Texel může být:  
  
-   `int`, `uint`, `float`, `double`, `norm`, Nebo `unorm` skalární.  
  
-   Krátký vektor, který má dva nebo čtyři součásti. Jedinou výjimkou je `double_4`, což není povolené.  
  
 `texture` Objekt může mít pořadí 1, 2 nebo 3. `texture` Objekt se dají zachytit pouze pomocí odkazu v argument lambda volání `parallel_for_each`. Textury jsou uloženy na GPU jako Direct3D – texture objekty. Další informace o textury a texels v Direct3D – najdete v tématu [Úvod do textury v Direct3D – 11](http://go.microsoft.com/fwlink/p/?linkid=248502).  
  
 Typ texel, které používáte, může být jedním z mnoha texture formáty, které se používají v programováním grafiky. Například formátu RGBA využít 32 bity s 8 bitů každý pro R, G, B a skalární elementy. Texture hardwaru grafické karty mají přístup k jednotlivé prvky založené na formátu. Například můžete hardwaru texture Pokud používáte formát RGBA, extrahujte každý prvek 8bitové do formuláře 32-bit. V C++ AMP můžete nastavit bity za skalární element vaší texel tak, aby bez použití bitovým posunutím automaticky přístup jednotlivé skalární elementy v kódu.  
  
### <a name="instantiating-texture-objects"></a>Vytváření instancí objektů textury  
 Je možné deklarovat objekt texture bez inicializace. Následující příklad kódu deklaruje několik texture objekty.  
  
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
  
 Můžete také použít konstruktor deklarovat a inicializovat `texture` objektu. Následující příklad kódu vytvoří `texture` objekt z vektor `float_4` objekty. Bity za skalární element nastavena na výchozí hodnoty. Nemůžete použít tento konstruktor s `norm`, `unorm`, nebo krátké vektorů `norm` a `unorm`, protože nemají výchozí bity za skalární elementu.  
  
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
  
 Můžete také deklarace a inicializace `texture` objekt pomocí konstruktoru přetížení, které přijímá ukazatel zdrojová data, velikost zdroje dat v bajtech a bity za skalární elementu.  
  
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
  
 Textury v těchto příkladech se vytvářejí na výchozí zobrazení akcelerátoru výchozí. Můžete použít další přetížení konstruktoru, pokud chcete určit `accelerator_view` objektu. Nelze vytvořit objekt texture na akcelerátor procesoru.  
  
 Existují omezení velikosti jednotlivých dimenze `texture` objektu, jak je znázorněno v následující tabulce. Pokud překročí mezní hodnoty, je vygenerována chyba spuštění.  
  
|Textura|Velikost omezenou na dimenzi|  
|-------------|---------------------|  
|Texture\<T, 1 >|16384|  
|Texture\<T, 2 >|16384|  
|Texture\<T, 3 >|2048|  
  
### <a name="reading-from-texture-objects"></a>Čtení z Texture objektů  
 Můžete číst z `texture` objekt pomocí [texture::operator\[\]](reference/texture-class.md#operator_at), [texture:: Operator() – operátor](reference/texture-class.md#operator_call), nebo [Texture::Get – metoda](reference/texture-class.md#get). Dva operátory vrátit hodnotu, není odkaz. Proto nemůže zapisovat do `texture` objekt pomocí `texture::operator\[\]`.  
  
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
  
 Následující příklad kódu ukazuje, jak ukládání texture kanály v krátké vektoru, a poté přístup k jednotlivé skalární elementy jako vlastnosti krátké vektoru.  
  
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
  
 Následující tabulka uvádí platný bitů na kanál pro každý typ vektoru řazení.  
  
|Texture datový typ|Platný bity za skalární – element|  
|-----------------------|-----------------------------------|  
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|  
|int_3 uint_3|32|  
|plovoucí desetinná čárka, float_2, float_4|16, 32|  
|float_3|32|  
|Dvojitý, double_2|64|  
|Norm, norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|  
  
### <a name="writing-to-texture-objects"></a>Zápis do Texture objekty  
 Použití [Texture::set –](reference/texture-class.md#set) metoda k zápisu do `texture` objekty. Objekt texture může být jen pro čtení nebo pro čtení a zápis. Pro objekt texture být možné číst a zapisovat musí být splněny následující podmínky:  

  
-   T má jenom jednu skalární součást. (Krátký vektory nejsou povoleny.)  
  
-   T není `double`, `norm`, nebo `unorm`.  
  
-   `texture::bits_per_scalar_element` Vlastnost je 32.  
  
 Pokud nejsou všechny tři nastavena hodnota true, pak se `texture` objekt je jen pro čtení. První dvě podmínky jsou kontrolovány během kompilace. Pokud máte kód, který se pokouší o zápis do je vygenerována chyba kompilace `readonly` texture objektu. Podmínky pro `texture::bits_per_scalar_element` je zjištěna v době běhu a generuje modul runtime [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) výjimka, pokud se pokusíte zapsat do jen pro čtení `texture` objektu.  
  
 Následující příklad kódu zapíše objekt texture hodnoty.  
  
```cpp  
void writeTexture() {  
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {      
    tex1.set(idx, 0);

 });

 
}  
 
```  
  
### <a name="copying-texture-objects"></a>Kopírování objektů textury  
 Můžete kopírovat mezi objekty texture pomocí [kopie](reference/concurrency-namespace-functions-amp.md#copy) funkce nebo [copy_async –](reference/concurrency-namespace-functions-amp.md#copy_async) fungovat, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Můžete také zkopírovat z jednoho texture na jiný pomocí [Texture::copy_to –](reference/texture-class.md#copy_to) metoda. Dva textury může být na různých accelerator_views. Pokud zkopírujete `writeonly_texture_view` objektu, ale data se zkopírují na odpovídající `texture` objektu. Bity za skalární elementu a v rozsahu musí být stejná ve zdrojové a cílové `texture` objekty. Pokud tyto požadavky nejsou splněny, modul runtime vyvolá výjimku.  

  
## <a name="texture-view-classes"></a>Texture třídy zobrazení  
 Zavádí C++ AMP [texture_view – třída](../../parallel/amp/reference/texture-view-class.md) v [!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)]. Texture zobrazení podporují stejné typy texel a pořadí jako [texture – třída](../../parallel/amp/reference/texture-class.md), ale na rozdíl od textury, poskytují přístup k funkcím další hardware, jako je například texture vzorkování a mipmaps. Texture zobrazení podporují přístup jen pro čtení, jen pro zápis a čtení a zápis v základních datech texture.  
  
-   Poskytuje přístup jen pro čtení `texture_view<const T, N>` specializace šablony, které podporuje prvky, které mají 1, 2 nebo 4 součásti, texture vzorkování a dynamické přístup k rozsah mipmap úrovní, které jsou určeny, když je vytvořena instance zobrazení.  
  
-   Poskytuje přístup jen pro zápis Nespecializovaný šablony třídy `texture_view<T, N>`, který podporuje prvky, které mají součásti 2 nebo 4 a přistupovat k jedné úrovni mipmap, které určil, když je vytvořena instance zobrazení. Vzorkování nepodporuje.  
  
-   Poskytuje přístup pro čtení a zápis Nespecializovaný šablony třídy `texture_view<T, N>`, který, jako je textury, podporuje prvky, které mají jenom jedna součást; zobrazení můžete přístup jednu úroveň mipmap, které určil, když je vytvořena instance. Vzorkování nepodporuje.  
  
 Texture zobrazení se podobá zobrazení pole, ale neposkytuje funkci správy a přesun dat, [array_view – třída](../../parallel/amp/reference/array-view-class.md) nabízí v porovnání s [array – třída](../../parallel/amp/reference/array-class.md). A `texture_view` jsou přístupné pouze na zobrazení akcelerátoru, kde se nachází v základních datech texture.  
  
### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view zastaralé  
 Pro [!INCLUDE[vs_dev12](../../atl-mfc-shared/includes/vs_dev12_md.md)], C++ AMP zavádí lepší podporu pro texture funkce hardwaru, například vzorkování a mipmaps, který nelze nepodporuje [writeonly_texture_view – třída](../../parallel/amp/reference/writeonly-texture-view-class.md). Nově přináší `texture_view` třída podporuje nadmnožinou funkce v `writeonly_texture_view`; v důsledku toho `writeonly_texture_view` je zastaralý.  
  
 Doporučujeme, abyste – aspoň pro nový kód – používaný `texture_view` do funkce přístupu, který byl dříve poskytované `writeonly_texture_view`. Porovnejte následující příklady dvě kódu, které zapsat do texture objekt, který má dvě součásti (int_2). Všimněte si, že v obou případech zobrazení, `wo_tv4`, musí být zachyceny hodnotu ve výrazu lambda. Tady je příklad, který používá nastavení nové `texture_view` třídy:  
  
```cpp  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 A tady je nepoužívané `writeonly_texture_view` třídy:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {     
    wo_tv4.set(idx, int_2(1, 1));

 });

}  
```  
  
 Jak můžete vidět, ukázky kódu dva jsou téměř shodná při všechny, které byste je na úroveň primární mipmap zápisu. Pokud jste použili `writeonly_texture_view` ve stávající kód a nemáte v plánu pro zlepšení, že kód, nemusíte ho změnit. Ale pokud uvažujete o uvedení tento kód předat dál, doporučujeme přepište ho na použití `texture_view` protože vylepšení v ní podporují nové funkce texture hardwaru. Přečtěte si další informace o tyto nové funkce.  
  
 Další informace o vyřazení nástroje `writeonly_texture_view`, najdete v části [přehled návrhu zobrazení Texture v C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) na paralelní programování v blogu nativního kódu.  
  
### <a name="instantiating-texture-view-objects"></a>Vytváření instancí objektů zobrazení textury  
 Deklarace `texture_view` je podobná deklarace `array_view` přidružená `array`. Následující příklad kódu deklaruje několik `texture` objekty a `texture_view` objekty, které jsou spojeny s nimi.  
  
```  
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
  
 Všimněte si, jak zobrazit texturou s typem elementu bez const a má jedna součást je pro čtení a zápis, ale texture zobrazení je jiný const s typem elementu, ale má více než jeden componenent jsou jen pro zápis. Typy const element Texture zobrazení jsou vždy jen pro čtení, ale pokud je typ elementu není const, pak počet součástí v elementu Určuje, zda je pro čtení a zápis (1 součást) nebo pouze pro zápis (více součástí).  
  
 Typ elementu `texture_view`– jeho const obchodní a také počet komponent má – také hrají roli při určování, zda zobrazení podporuje texture vzorkování, a jak je přístupná mipmap úrovně:  
  
|Typ|Součásti|Číst|Write|Vzorkování|Mipmap přístup|  
|----------|----------------|----------|-----------|--------------|-------------------|  
|texture_view\<const T, N >|1, 2, 4|Ano|Ne (1)|Ano|Ano, indexovanou. Rozsah určí při vytvoření instance.|  
|Texture_view\<T, N >|1<br /><br /> 2, 4|Ano<br /><br /> Ne (2)|Ano<br /><br /> Ano|Ne (1)<br /><br /> Ne (1)|Ano, jedna úroveň. Úroveň určí při vytvoření instance.<br /><br /> Ano, jedna úroveň. Úroveň určí při vytvoření instance.|  
  
 Z této tabulky uvidíte, že zobrazení jen pro čtení texture plně podporují nové možnosti za nebude moci zapisovat do zobrazení. V tom, že mají přístup pouze jedna úroveň mipmap jsou omezené zapisovatelné texture zobrazení. Zobrazení pro čtení a zápis texture jsou specializované i více než zapisovatelné těch, protože zvyšují požadavek, že typ elementu texture zobrazení má jenom jedna součást. Všimněte si, že vzorkování není podporována pro zobrazení s možností zápisu texture protože se jedná o operaci čtení.  
  
### <a name="reading-from-texture-view-objects"></a>Čtení ze Texture objekty zobrazení  
 Čtení dat unsampled texture prostřednictvím zobrazení texture je stejně jako jeho čtení z texture samostatně, ale textury jsou zachycenou referenční, zatímco texture zobrazení jsou zachyceny hodnotu. Následující příklady dvě kódu ukazují; první pomocí `texture` pouze:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {  
    tex_data.set(idx, int_2(1, 1));

 });

}  
```  
  
 A zde je stejný, s výjimkou teď používá `texture_view` třídy:  
  
```  
void write2ComponentTexture() {  
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {  
    tex_view.set(idx, int_2(1, 1));

 });

}  
```  
 Texture zobrazení, jehož elementy jsou založené na typy s plovoucí desetinnou čárkou – například float, float_2 nebo float_4 – můžete také pro čtení s použitím vzorkování texture Pokud chcete využít výhod podpory hardwaru pro různé režimy filtrování a adresování režimy. C++ AMP podporuje dva filtrování režimy, které jsou nejběžnější způsoby výpočetní – bod filtrování (nejbližší sousedním) a lineární filtrování (váženým průměrem) – a čtyři adresování režimy – uzavřen, zrcadlení, těsně a ohraničení. Další informace o adresování režimech najdete v tématu [address_mode – výčet](reference/concurrency-graphics-namespace-enums.md#address_mode).  
  
 Kromě režimy, které podporuje C++ AMP přímo můžete pomocí zprostředkovatele komunikace s objekty rozhraní API přijmout texture sampler, který byl vytvořen přímo pomocí platformy API přístup další filtrování a adresování režimů základní platformy. Direct3D – například podporuje další filtrování režimy například volba filtrování a můžou použít jiný režim adresování Každá dimenze texturou. Můžete vytvořit texture sampler zabalené svisle, vodorovně zrcadlení a vzorkovat jejichž souřadnice s volba filtrování pomocí rozhraní API Direct3D – a pak ho využít ve vašem kódu C++ AMP pomocí `make_sampler` spolupráce rozhraní API. Další informace najdete v části [Texture vzorkování v C++ AMP](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) na paralelní programování v blogu nativního kódu.  
  
 Texture zobrazení také podporují čtení mipmaps. Zobrazení jen pro čtení texture, (ty, které mají const typ elementu) nabízejí nejvíce flexibilitu, protože rozsah mip úrovně, které určí při vytvoření instance se dá dynamicky vzorkovat a vzhledem k tomu, že jsou podporovány elementy, které mají 1, 2 nebo 4 součásti. Čtení a zápis texture zobrazení, která mají prvky, které mají jednu součást také podporují mipmaps, ale jenom úrovně, který určí při vytvoření instance. Další informace najdete v tématu [Texture s Mipmaps](http://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) na paralelní programování v blogu nativního kódu.  
  
### <a name="writing-to-texture-view-objects"></a>Zápis do Texture objekty zobrazení  
 Použití [texture_view::Get – metoda](reference/texture-view-class.md#get) k zápisu do základní `texture` prostřednictvím `texture_view` objektu. Texture zobrazení může být jen pro čtení, čtení a zápis nebo jen pro zápis. Pro zobrazení texture být zapisovatelný musí mít typ elementu, který je jiný const; pro zobrazení texture čtení a zápis její typ elementu musí rovněž mít pouze jednu součást. Texture zobrazení, jinak je jen pro čtení. Můžete pouze jeden mipmap úroveň přístupu tohoto texturou v čase prostřednictvím texture zobrazení a úroveň je zadána při vytváření instance zobrazení.  
  
 Tento příklad ukazuje, jak k zápisu do podrobné mipmap sekundu většinu úroveň texture, který má 4 mipmap úrovně. Úroveň nejpodrobnější mipmap je 0.  
  
```  
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

 Modul runtime C++ AMP podporuje spolupráci mezi `texture<T,1>` a [ID3D11Texture1D rozhraní](http://go.microsoft.com/fwlink/p/?linkId=248503), mezi `texture<T,2>` a [ID3D11Texture2D rozhraní](http://go.microsoft.com/fwlink/p/?linkId=255317)a mezi `texture<T,3>`a [ID3D11Texture3D rozhraní](http://go.microsoft.com/fwlink/p/?linkId=255377). [Get_texture –](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) metoda trvá `texture` objekt a vrátí `IUnknown` rozhraní. [Make_texture –](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) metoda trvá `IUnknown` rozhraní a `accelerator_view` objekt a vrátí `texture` objektu.  
  
## <a name="see-also"></a>Viz také  
 [double_2 – třída](../../parallel/amp/reference/double-2-class.md)   
 [double_3 – třída](../../parallel/amp/reference/double-3-class.md)   
 [double_4 – třída](../../parallel/amp/reference/double-4-class.md)   
 [float_2 – třída](../../parallel/amp/reference/float-2-class.md)   
 [float_3 – třída](../../parallel/amp/reference/float-3-class.md)   
 [float_4 – třída](../../parallel/amp/reference/float-4-class.md)   
 [int_2 – třída](../../parallel/amp/reference/int-2-class.md)   
 [int_3 – třída](../../parallel/amp/reference/int-3-class.md)   
 [int_4 – třída](../../parallel/amp/reference/int-4-class.md)   
 [norm_2 – třída](../../parallel/amp/reference/norm-2-class.md)   
 [norm_3 – třída](../../parallel/amp/reference/norm-3-class.md)   
 [norm_4 – třída](../../parallel/amp/reference/norm-4-class.md)   
 [short_vector – struktura](../../parallel/amp/reference/short-vector-structure.md)   
 [short_vector_traits – struktura](../../parallel/amp/reference/short-vector-traits-structure.md)   
 [uint_2 – třída](../../parallel/amp/reference/uint-2-class.md)   
 [uint_3 – třída](../../parallel/amp/reference/uint-3-class.md)   
 [uint_4 – třída](../../parallel/amp/reference/uint-4-class.md)   
 [unorm_2 – třída](../../parallel/amp/reference/unorm-2-class.md)   
 [unorm_3 – třída](../../parallel/amp/reference/unorm-3-class.md)   
 [unorm_4 – třída](../../parallel/amp/reference/unorm-4-class.md)
