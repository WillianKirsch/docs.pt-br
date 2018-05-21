### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a><span data-ttu-id="78b70-101">Icon.ToBitmap converte com êxito ícones com quadros PNG em objetos Bitmap</span><span class="sxs-lookup"><span data-stu-id="78b70-101">Icon.ToBitmap successfully converts icons with PNG frames into Bitmap objects</span></span>

|   |   |
|---|---|
|<span data-ttu-id="78b70-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="78b70-102">Details</span></span>|<span data-ttu-id="78b70-103">Começando com os aplicativos direcionados ao .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> converte com êxito ícones com quadros PNG em objetos Bitmap.</span><span class="sxs-lookup"><span data-stu-id="78b70-103">Starting with the apps that target the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into Bitmap objects.</span></span><p/><span data-ttu-id="78b70-104">Nos aplicativos direcionados ao .NET Framework 4.5.2 e a versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> gera uma exceção <xref:System.ArgumentOutOfRangeException> quando o objeto Ícone tem quadros PNG.</span><span class="sxs-lookup"><span data-stu-id="78b70-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the  <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the Icon object has PNG frames.</span></span><p/><span data-ttu-id="78b70-105">Essa alteração afeta os aplicativos que são recompilados para serem direcionados ao .NET Framework 4.6 e que implementam um tratamento especial para a <xref:System.ArgumentOutOfRangeException>, que será gerada quando um objeto Ícone tiver quadros PNG.</span><span class="sxs-lookup"><span data-stu-id="78b70-105">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an Icon object has PNG frames.</span></span> <span data-ttu-id="78b70-106">Ao executar no .NET Framework 4.6, a conversão é bem-sucedida, uma <xref:System.ArgumentOutOfRangeException> não é mais gerada e, portanto, o manipulador de exceção não é invocado.</span><span class="sxs-lookup"><span data-stu-id="78b70-106">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>|
|<span data-ttu-id="78b70-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="78b70-107">Suggestion</span></span>|<span data-ttu-id="78b70-108">Se esse comportamento for indesejável, será possível reter o comportamento anterior adicionando o seguinte elemento à seção <code>&lt;runtime&gt;</code> do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="78b70-108">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre><span data-ttu-id="78b70-109">Se o arquivo app.config já contiver o elemento <code>AppContextSwitchOverrides</code>, o novo valor deverá ser mesclado ao atributo de valor, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="78b70-109">If the app.config file already contains the <code>AppContextSwitchOverrides</code> element, the new value should be merged with the value attribute like this:</span></span><pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="78b70-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="78b70-110">Scope</span></span>|<span data-ttu-id="78b70-111">Secundário</span><span class="sxs-lookup"><span data-stu-id="78b70-111">Minor</span></span>|
|<span data-ttu-id="78b70-112">Versão</span><span class="sxs-lookup"><span data-stu-id="78b70-112">Version</span></span>|<span data-ttu-id="78b70-113">4.6</span><span class="sxs-lookup"><span data-stu-id="78b70-113">4.6</span></span>|
|<span data-ttu-id="78b70-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="78b70-114">Type</span></span>|<span data-ttu-id="78b70-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="78b70-115">Retargeting</span></span>|
|<span data-ttu-id="78b70-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="78b70-116">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
