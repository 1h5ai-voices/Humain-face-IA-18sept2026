(function () {
  function setLang(lang) {
    document.querySelectorAll(".lang-content").forEach(function (el) {
      el.classList.toggle("active", el.getAttribute("data-lang") === lang);
    });
    document.querySelectorAll(".lang-toggle button").forEach(function (btn) {
      btn.classList.toggle("active", btn.getAttribute("data-lang") === lang);
    });
    document.querySelectorAll("[data-fr][data-en]").forEach(function (el) {
      el.textContent = lang === "fr" ? el.getAttribute("data-fr") : el.getAttribute("data-en");
    });
    try { localStorage.setItem("6voices-lang", lang); } catch (e) {}
  }

  document.addEventListener("DOMContentLoaded", function () {
    var saved = "fr";
    try { saved = localStorage.getItem("6voices-lang") || "fr"; } catch (e) {}
    setLang(saved);

    document.querySelectorAll(".lang-toggle button").forEach(function (btn) {
      btn.addEventListener("click", function () {
        setLang(btn.getAttribute("data-lang"));
      });
    });
  });
})();
