<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <title>ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่น</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>

    <style>
      /* กำหนดสีให้คล้ายโปรเจกต์เดิม */
      :root {
        --thai-primary: #059669;      /* emerald-600 */
        --thai-secondary: #0f766e;    /* teal-700 */
        --thai-accent: #a7f3d0;       /* emerald-200 */
        --ministry-orange: #ea580c;   /* orange-600 */
      }

      .bg-thai-primary { background-color: var(--thai-primary); }
      .bg-thai-secondary { background-color: var(--thai-secondary); }
      .bg-thai-accent { background-color: var(--thai-accent); }
      .text-thai-primary { color: var(--thai-primary); }
      .text-thai-secondary { color: var(--thai-secondary); }
      .text-ministry-orange { color: var(--ministry-orange); }
      .border-thai-secondary { border-color: var(--thai-secondary); }

      @keyframes fade-in {
        from { opacity: 0; transform: translateY(6px); }
        to { opacity: 1; transform: translateY(0); }
      }
      .animate-fade-in { animation: fade-in 0.4s ease-out; }
    </style>
  </head>

  <body class="bg-gray-50 min-h-screen flex flex-col">
    <!-- Header -->
    <header class="bg-thai-primary shadow-lg text-white sticky top-0 z-50">
      <div
        class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col md:flex-row items-center justify-between"
      >
        <div class="flex items-center space-x-4">
          <div
            class="bg-white/10 p-2.5 rounded-lg backdrop-blur-sm border border-white/20 shadow-inner"
          >
            <!-- icon หนังสือ -->
            <span class="text-thai-secondary text-2xl">📚</span>
          </div>
          <div>
            <h1
              class="text-xl md:text-2xl font-bold leading-tight tracking-tight"
            >
              ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่น
            </h1>
            <p
              class="text-sm text-teal-100 font-medium opacity-90 flex items-center gap-1"
            >
              <span class="text-xs">📍</span>
              เชื่อมโยงมาตรฐาน/ตัวชี้วัด หลักสูตรแกนกลางฯ
            </p>
          </div>
        </div>
      </div>
    </header>

    <!-- Main -->
    <main class="flex-1">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <!-- Hero -->
        <section class="text-center py-8 md:py-12 px-4 animate-fade-in">
          <div
            class="inline-flex items-center justify-center p-4 bg-white rounded-full shadow-md mb-6"
          >
            <span class="text-thai-secondary text-3xl animate-pulse">🧭</span>
          </div>
          <h2
            class="text-3xl md:text-4xl font-bold text-gray-800 mb-6 tracking-tight leading-tight"
          >
            ค้นหาแหล่งเรียนรู้
            <span class="text-thai-primary block md:inline md:ml-2"
              >ใกล้ตัวคุณ</span
            >
          </h2>
          <p
            class="text-gray-600 max-w-2xl mx-auto text-lg leading-relaxed"
          >
            ระบบช่วยให้ครูและนักเรียนสามารถสำรวจแหล่งเรียนรู้ในชุมชน
            และเชื่อมโยงกับสาระการเรียนรู้/มาตรฐานของหลักสูตรแกนกลางฯ
            เพื่อออกแบบการเรียนรู้ที่สอดคล้องกับบริบทพื้นที่
          </p>
        </section>

        <!-- Search Form -->
        <section
          class="bg-white rounded-xl shadow-md border border-gray-200 p-6 mb-8 relative overflow-hidden"
        >
          <div
            class="absolute top-0 right-0 w-32 h-32 bg-thai-accent rounded-full -mr-10 -mt-10 opacity-50 z-0 pointer-events-none"
          ></div>

          <div class="relative z-10">
            <h2
              class="text-lg font-semibold text-gray-800 mb-4 flex items-center gap-2"
            >
              <span class="text-thai-primary text-xl">🗺️</span>
              ค้นหาแหล่งเรียนรู้ท้องถิ่น
            </h2>

            <form
              id="search-form"
              class="grid grid-cols-1 md:grid-cols-3 gap-6 items-end"
            >
              <!-- Province -->
              <div>
                <label
                  for="province"
                  class="block text-sm font-medium text-gray-700 mb-1"
                >
                  จังหวัด <span class="text-red-500">*</span>
                </label>
                <div class="relative">
                  <select
                    id="province"
                    class="mt-1 block w-full rounded-lg border-gray-300 bg-gray-50 border py-2.5 px-3 shadow-sm focus:ring-thai-primary focus:border-thai-primary sm:text-sm transition-colors cursor-pointer hover:bg-white"
                  >
                    <option value="">-- เลือกจังหวัด --</option>
                  </select>
                </div>
              </div>

              <!-- District -->
              <div>
                <label
                  for="district"
                  class="block text-sm font-medium text-gray-700 mb-1"
                >
                  อำเภอ/เขต
                </label>
                <div class="relative">
                  <select
                    id="district"
                    disabled
                    class="mt-1 block w-full rounded-lg border border-gray-300 py-2.5 px-3 shadow-sm focus:ring-thai-primary focus:border-thai-primary sm:text-sm transition-all bg-gray-100 text-gray-400 cursor-not-allowed"
                  >
                    <option value="">-- เลือกอำเภอ/เขต (ทั้งหมด) --</option>
                  </select>
                </div>
              </div>

              <!-- Submit Button -->
              <div class="flex md:justify-end">
                <button
                  id="search-button"
                  type="submit"
                  class="inline-flex items-center justify-center w-full md:w-auto px-6 py-2.5 rounded-lg text-white text-sm font-medium shadow-md transition-all transform active:scale-95 bg-thai-primary hover:bg-emerald-700 hover:shadow-lg"
                >
                  <span class="flex items-center gap-2">
                    <span class="text-sm">🔍</span>
                    ค้นหา
                  </span>
                </button>
              </div>
            </form>
          </div>
        </section>

        <!-- Results Container -->
        <section id="results-section">
          <!-- จะถูกเติมด้วย JS: header + list หรือ empty state -->
        </section>
      </div>
    </main>

    <!-- Footer -->
    <footer
      class="bg-gray-800 text-gray-400 py-8 mt-auto border-t border-gray-700"
    >
      <div class="max-w-7xl mx-auto px-4 text-center">
        <p class="text-sm font-light">
          © <span id="footer-year"></span>
          ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่นเพื่อการศึกษาไทย
        </p>
        <p class="text-xs text-gray-500 mt-2">
          พัฒนาเพื่อการศึกษาและพัฒนาชุมชนอย่างยั่งยืน
        </p>
      </div>
    </footer>

    <!-- JavaScript -->
    <script>
      // ----------------------------
      // ข้อมูลจังหวัด & อำเภอ (ตัวอย่างย่อ)
      // คุณสามารถขยายเพิ่มเติมได้เองตาม constants.ts
      // ----------------------------
      const THAI_PROVINCES = [
        "กรุงเทพมหานคร",
        "เชียงใหม่",
        "เชียงราย",
        "นครราชสีมา",
        "ขอนแก่น",
        "ชลบุรี"
      ];

      const PROVINCE_DISTRICTS = {
        "กรุงเทพมหานคร": [
          "พระนคร",
          "ดุสิต",
          "หนองจอก",
          "บางรัก",
          "บางเขน",
          "บางกะปิ"
        ],
        "เชียงใหม่": [
          "เมืองเชียงใหม่",
          "จอมทอง",
          "แม่แจ่ม",
          "เชียงดาว",
          "แม่แตง"
        ],
        "เชียงราย": [
          "เมืองเชียงราย",
          "เวียงชัย",
          "เชียงของ",
          "เทิง",
          "พาน"
        ],
        "นครราชสีมา": [
          "เมืองนครราชสีมา",
          "ครบุรี",
          "เสิงสาง",
          "คง",
          "ขามทะเลสอ"
        ],
        "ขอนแก่น": [
          "เมืองขอนแก่น",
          "บ้านฝาง",
          "พระยืน",
          "หนองเรือ",
          "ชุมแพ"
        ],
        "ชลบุรี": [
          "เมืองชลบุรี",
          "บ้านบึง",
          "หนองใหญ่",
          "บางละมุง",
          "พานทอง"
        ]
      };

      // ----------------------------
      // ตัวอย่างข้อมูลแหล่งเรียนรู้ (ย่อจาก SAMPLE_RESOURCES)
      // ----------------------------
      const SAMPLE_RESOURCES = [
        {
          id: "bkk-1",
          name: "วัดพระแก้ว และพระบรมมหาราชวัง",
          province: "กรุงเทพมหานคร",
          district: "พระนคร",
          description:
            "แหล่งเรียนรู้ด้านศิลปวัฒนธรรม ประวัติศาสตร์ และสถาปัตยกรรมไทย สำคัญระดับชาติ เหมาะกับการจัดการเรียนรู้แบบบูรณาการหลายกลุ่มสาระ",
          subjects: ["สังคมศึกษา", "ประวัติศาสตร์", "ศิลปะ"],
          standards: ["ส 4.1 เข้าใจพัฒนาการของไทย", "ศ 1.1 ชื่นชมศิลปวัฒนธรรมไทย"],
          tags: ["โบราณสถาน", "วัฒนธรรม", "พระราชวัง"],
          imageUrl: "https://picsum.photos/seed/bkk-1/600/400"
        },
        {
          id: "bkk-2",
          name: "พิพิธภัณฑสถานแห่งชาติ พระนคร",
          province: "กรุงเทพมหานคร",
          district: "พระนคร",
          description:
            "ศูนย์เรียนรู้เกี่ยวกับโบราณวัตถุ ศิลปวัตถุ และประวัติศาสตร์ชาติไทย เหมาะสำหรับการเรียนรู้เชิงสืบเสาะและการจัดทำโครงงาน",
          subjects: ["สังคมศึกษา", "ประวัติศาสตร์"],
          standards: ["ส 4.3 วิเคราะห์หลักฐานทางประวัติศาสตร์"],
          tags: ["พิพิธภัณฑ์", "ประวัติศาสตร์"],
          imageUrl: "https://picsum.photos/seed/bkk-2/600/400"
        },
        {
          id: "chiangmai-1",
          name: "วัดพระธาตุดอยสุเทพราชวรวิหาร",
          province: "เชียงใหม่",
          district: "เมืองเชียงใหม่",
          description:
            "แหล่งเรียนรู้ด้านศาสนา ประวัติศาสตร์ท้องถิ่น และภูมิศาสตร์กายภาพ มองเห็นภาพรวมเมืองเชียงใหม่จากมุมสูง",
          subjects: ["สังคมศึกษา", "ภูมิศาสตร์"],
          standards: ["ส 1.1 ศาสนากับวิถีชีวิต", "ส 5.1 ภูมิศาสตร์ท้องถิ่น"],
          tags: ["วัด", "ภูเขา", "แหล่งท่องเที่ยว"],
          imageUrl: "https://picsum.photos/seed/cm-1/600/400"
        },
        {
          id: "chon-1",
          name: "พิพิธภัณฑ์พุทธมณฑล อำเภอเมืองชลบุรี",
          province: "ชลบุรี",
          district: "เมืองชลบุรี",
          description:
            "แหล่งเรียนรู้เรื่องพระพุทธศาสนา ศิลปะไทย และการดำเนินชีวิตตามหลักธรรม เหมาะกับการจัดกิจกรรมโครงงานคุณธรรม",
          subjects: ["สังคมศึกษา", "ศิลปะ"],
          standards: ["ส 1.1", "ศ 1.1"],
          tags: ["ศาสนา", "วัฒนธรรม"],
          imageUrl: "https://picsum.photos/seed/chon-1/600/400"
        }
      ];

      // ----------------------------
      // utility: สร้าง fallback resource ถ้าไม่พบข้อมูลในอำเภอนั้น
      // ----------------------------
      function createFallbackResources(province, district) {
        const cityDistrict = district || "เมือง" + province;
        return [
          {
            id: `fallback-temple-${province}-${district || "all"}`,
            name: `วัดประจำอำเภอ${cityDistrict}`,
            province,
            district: cityDistrict,
            description:
              "วัดในชุมชนซึ่งสามารถใช้เป็นแหล่งเรียนรู้เรื่องศาสนา วัฒนธรรม วิถีชีวิต และภูมิปัญญาท้องถิ่น นักเรียนสามารถเก็บข้อมูล สัมภาษณ์ และสร้างโครงงานได้",
            subjects: ["สังคมศึกษา", "ภาษาไทย"],
            standards: ["ส 1.1", "ท 1.1"],
            tags: ["วัด", "ชุมชน", "ภูมิปัญญาท้องถิ่น"],
            imageUrl: "https://picsum.photos/seed/fallback-temple/600/400"
          },
          {
            id: `fallback-cultural-${province}-${district || "all"}`,
            name: `ศูนย์วัฒนธรรมท้องถิ่นอำเภอ${cityDistrict}`,
            province,
            district: cityDistrict,
            description:
              "แหล่งรวบรวมข้อมูลประวัติศาสตร์ ท้องถิ่น ภูมิปัญญา และงานหัตถกรรมพื้นบ้าน เหมาะสำหรับจัดการเรียนรู้แบบโครงงาน (Project-based Learning)",
            subjects: ["สังคมศึกษา", "ประวัติศาสตร์"],
            standards: ["ส 4.1", "ส 4.3"],
            tags: ["วัฒนธรรม", "ประวัติศาสตร์", "ชุมชน"],
            imageUrl: "https://picsum.photos/seed/fallback-cultural/600/400"
          }
        ];
      }

      // ----------------------------
      // DOM elements
      // ----------------------------
      const provinceSelect = document.getElementById("province");
      const districtSelect = document.getElementById("district");
      const searchForm = document.getElementById("search-form");
      const searchButton = document.getElementById("search-button");
      const resultsSection = document.getElementById("results-section");
      const footerYear = document.getElementById("footer-year");

      footerYear.textContent = new Date().getFullYear();

      // ----------------------------
      // เติมจังหวัดลง select
      // ----------------------------
      function populateProvinces() {
        THAI_PROVINCES.sort((a, b) => a.localeCompare(b, "th"));
        THAI_PROVINCES.forEach((p) => {
          const option = document.createElement("option");
          option.value = p;
          option.textContent = p;
          provinceSelect.appendChild(option);
        });
      }

      populateProvinces();

      // ----------------------------
      // เมื่อเปลี่ยนจังหวัด -> โหลดอำเภอ
      // ----------------------------
      provinceSelect.addEventListener("change", () => {
        const province = provinceSelect.value;
        const districts = PROVINCE_DISTRICTS[province] || [];

        // reset district select
        districtSelect.innerHTML =
          '<option value="">-- เลือกอำเภอ/เขต (ทั้งหมด) --</option>';

        if (districts.length > 0) {
          districts
            .slice()
            .sort((a, b) => a.localeCompare(b, "th"))
            .forEach((d) => {
              const opt = document.createElement("option");
              opt.value = d;
              opt.textContent = d;
              districtSelect.appendChild(opt);
            });

          districtSelect.disabled = false;
          districtSelect.classList.remove(
            "bg-gray-100",
            "text-gray-400",
            "cursor-not-allowed"
          );
          districtSelect.classList.add("bg-gray-50", "cursor-pointer");
        } else {
          districtSelect.disabled = true;
          districtSelect.classList.add(
            "bg-gray-100",
            "text-gray-400",
            "cursor-not-allowed"
          );
          districtSelect.classList.remove("bg-gray-50", "cursor-pointer");
        }
      });

      // ----------------------------
      // ฟังก์ชัน render: Empty State
      // ----------------------------
      function renderEmptyState() {
        resultsSection.innerHTML = `
          <div class="text-center py-20 bg-white rounded-xl shadow-sm border border-dashed border-gray-300 animate-fade-in">
            <div class="bg-gray-50 w-24 h-24 rounded-full flex items-center justify-center mx-auto mb-4">
              <span class="text-3xl text-gray-400">🔎</span>
            </div>
            <p class="text-gray-600 text-lg font-medium">ไม่พบข้อมูลแหล่งเรียนรู้</p>
            <p class="text-gray-400 text-sm mt-1">
              ลองเปลี่ยนคำค้นหาอำเภอ หรือค้นหาเฉพาะระดับจังหวัด
            </p>
          </div>
        `;
      }

      // ----------------------------
      // ฟังก์ชันสร้าง HTML ของ Resource Card
      // ----------------------------
      function createResourceCardHTML(resource) {
        const standardsList = resource.standards || [];
        const tagsList = resource.tags || [];
        const subjectsList = resource.subjects || [];

        const shownStandards = standardsList.slice(0, 2);
        const extraCount =
          standardsList.length > 2 ? standardsList.length - 2 : 0;

        return `
          <article class="bg-white rounded-xl shadow-md hover:shadow-xl border border-gray-200 overflow-hidden flex flex-col transition-all duration-300 transform hover:-translate-y-1 group h-full">
            <!-- Header -->
            <div class="bg-gradient-to-r from-thai-accent to-white px-5 py-4 border-b border-gray-100 relative">
              <div class="absolute top-0 left-0 w-1 h-full bg-thai-secondary"></div>
              <h4 class="font-bold text-gray-800 text-lg line-clamp-2 group-hover:text-thai-primary transition-colors h-14 flex items-center">
                ${resource.name}
              </h4>
              <div class="flex items-center gap-1 text-xs text-gray-500 mt-1.5">
                <span class="text-xs">📍</span>
                <span class="truncate">จ.${resource.province} • อ.${resource.district}</span>
              </div>
            </div>

            <!-- Image -->
            <div class="h-48 bg-gray-100 w-full overflow-hidden relative">
              <img
                src="${resource.imageUrl || "https://picsum.photos/seed/default/600/400"}"
                alt="${resource.name}"
                class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
                loading="lazy"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-black/30 to-transparent opacity-60 group-hover:opacity-40 transition-opacity"></div>
            </div>

            <!-- Content -->
            <div class="p-5 flex flex-col gap-4 flex-grow">
              <p class="text-sm text-gray-600 leading-relaxed line-clamp-3 min-h-[4.5em]">
                ${resource.description || ""}
              </p>

              <div class="space-y-3 mt-auto">
                <!-- Subjects -->
                <div class="text-xs">
                  <p class="font-semibold text-gray-700 mb-1.5 flex items-center gap-1.5">
                    <span class="text-[13px]">📘</span>
                    สาระการเรียนรู้:
                  </p>
                  <p class="text-gray-600 pl-5 line-clamp-1">
                    ${subjectsList.join(" • ")}
                  </p>
                </div>

                <!-- Standards -->
                <div class="text-xs bg-gray-50 p-2.5 rounded-lg border border-gray-100">
                  <p class="font-semibold text-gray-700 mb-1.5 flex items-center gap-1.5">
                    <span class="text-ministry-orange text-[13px]">✔️</span>
                    มาตรฐาน/ตัวชี้วัด:
                  </p>
                  <ul class="text-gray-600 space-y-1 pl-1">
                    ${shownStandards
                      .map(
                        (s) => `
                        <li class="flex items-start gap-1.5 line-clamp-1">
                          <span class="block w-1 h-1 rounded-full bg-gray-400 mt-1.5 flex-shrink-0"></span>
                          <span>${s}</span>
                        </li>
                      `
                      )
                      .join("")}
                    ${
                      extraCount > 0
                        ? `<li class="pl-2.5 text-gray-400 italic">...และอื่นๆ อีก ${extraCount} รายการ</li>`
                        : ""
                    }
                  </ul>
                </div>
              </div>

              <!-- Tags -->
              <div class="pt-3 border-t border-gray-100 flex flex-wrap gap-2">
                ${tagsList
                  .slice(0, 3)
                  .map(
                    (t) => `
                    <span
                      class="inline-flex items-center gap-1 px-2.5 py-1 rounded-full bg-teal-50 text-[11px] font-medium text-thai-primary border border-teal-100 whitespace-nowrap"
                    >
                      <span class="text-[11px]">🏷️</span>
                      ${t}
                    </span>
                  `
                  )
                  .join("")}
              </div>
            </div>
          </article>
        `;
      }

      // ----------------------------
      // render Resource List
      // ----------------------------
      function renderResources(resources) {
        if (!resources || resources.length === 0) {
          renderEmptyState();
          return;
        }

        const headerHTML = `
          <div class="flex items-center justify-between mb-6 animate-fade-in">
            <h3 class="text-lg font-semibold text-gray-700 border-l-4 border-thai-secondary pl-3">
              ผลการค้นหา:
              <span class="text-thai-primary font-bold text-xl">${resources.length}</span>
              รายการ
            </h3>
            <span class="hidden sm:inline-block text-xs text-gray-500 bg-white border border-gray-200 px-3 py-1 rounded-full shadow-sm">
              Local Learning Resources
            </span>
          </div>
        `;

        const gridHTML = `
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            ${resources.map((r) => createResourceCardHTML(r)).join("")}
          </div>
        `;

        resultsSection.innerHTML = headerHTML + gridHTML;
      }

      // ----------------------------
      // handle submit
      // ----------------------------
      searchForm.addEventListener("submit", (e) => {
        e.preventDefault();
        const province = provinceSelect.value.trim();
        const district = districtSelect.value.trim();

        if (!province) {
          alert("กรุณาเลือกจังหวัดก่อนทำการค้นหา");
          return;
        }

        // ปุ่ม loading เล็กน้อย (สั้น ๆ)
        searchButton.disabled = true;
        searchButton.classList.add("opacity-80", "cursor-not-allowed");
        searchButton.innerHTML = `
          <span class="flex items-center gap-2">
            <span class="animate-spin inline-block">⏳</span>
            กำลังค้นหา...
          </span>
        `;

        setTimeout(() => {
          // filter resources
          let results = SAMPLE_RESOURCES.filter((r) => r.province === province);
          if (district) {
            results = results.filter((r) => r.district === district);
          }

          // ถ้าไม่พบ แต่มีระบุอำเภอ -> สร้าง fallback
          if (results.length === 0 && district) {
            results = createFallbackResources(province, district);
          } else if (results.length === 0 && !district) {
            // ถ้าไม่พบทั้งจังหวัด (ไม่มีอำเภอ) -> สร้าง fallback สำหรับจังหวัด
            results = createFallbackResources(province, "");
          }

          renderResources(results);

          // reset ปุ่ม
          searchButton.disabled = false;
          searchButton.classList.remove("opacity-80", "cursor-not-allowed");
          searchButton.innerHTML = `
            <span class="flex items-center gap-2">
              <span class="text-sm">🔍</span>
              ค้นหา
            </span>
          `;
        }, 300);
      });

      // แสดง empty state ครั้งแรก
      renderEmptyState();
    </script>
  </body>
</html>
