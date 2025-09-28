# WAKUBWA-TUU
Chagua mkoa wako ili upate pisikali ya mtaani kwako sasahivi uttombe
{
  "regions": [
    {
      "name": "Arusha",
      "districts": [
        {
          "name": "Arusha Urban",
          "wards": [
            { "name": "Kati", "message": "" },
            { "name": "Sombetini", "message": "" },
            { "name": "Urunduru", "message": "" }
          ]
        },
        {
          "name": "Karatu",
          "wards": [
            { "name": "Karatu", "message": "" },
            { "name": "Mang'ola", "message": "" }
          ]
        }
      ]
    },
    {
      "name": "Dar es Salaam",
      "districts": [
        {
          "name": "Kinondoni",
          "wards": [
            { "name": "Mikocheni", "message": "" },
            { "name": "Magomeni", "message": "" },
            { "name": "Kigogo", "message": "" }
          ]
        },
        {
          "name": "Ilala",
          "wards": [
            { "name": "Upanga East", "message": "" },
            { "name": "Upanga West", "message": "" },
            { "name": "Jangwani", "message": "" }
          ]
        }
      ]
    }
    // na mikoa mingine ifuatayo...
  ]
}
    const districtsContainer = regionElement.querySelector('.districts');
    if (districtsContainer) {
      districtsContainer.style.display = districtsContainer.style.display === 'none' ? 'block' : 'none';
    }
  }

  function toggleVillages(regionName, districtName) {
    const regionElement = document.getElementById(regionName);
    const districtElement = regionElement.querySelector(`#${districtName}`);
    const villagesContainer = districtElement.querySelector('.villages');
    if (villagesContainer) {
      villagesContainer.style.display = villagesContainer.style.display === 'none' ? 'block' : 'none';
    }
  }

  function showMessage() {
    message.style.display = 'block';
    setTimeout(() => {
      message.style.display = 'none';
    }, 5000);
  }

  function buildRegions() {
    for (const regionName in data) {
      const regionElement = createRegionElement(regionName);
      regionElement.id = regionName;
      const districtsContainer = document.createElement('div');
      districtsContainer.classList.add('districts');
      for (const districtName in data[regionName]) {
        const districtElement = createDistrictElement(regionName, districtName);
        districtElement.id = districtName;
        const villagesContainer = document.createElement('div');
        villagesContainer.classList.add('villages');
        data[regionName][districtName].forEach(villageName => {
          const villageElement = createVillageElement(regionName, districtName, villageName);
          villagesContainer.appendChild(villageElement);
        });
        districtElement.appendChild(villagesContainer);
        districtsContainer.appendChild(districtElement);
      }
      regionElement.appendChild(districtsContainer);
      regionsContainer.appendChild(regionElement);
    }
  }

  buildRegions();
</script>

</body>
</html>
