<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Wemert Group Realty</title>

  <style>
    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background-color: #f2f4f7;
    }

    header {
      background-color: #0a2a66;
      color: white;
      padding: 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
    }

    .container {
      padding: 15px;
    }

    .search-box {
      background: white;
      padding: 15px;
      border-radius: 8px;
      margin-bottom: 20px;
    }

    .search-box input,
    .search-box button {
      width: 100%;
      padding: 12px;
      margin-top: 10px;
      font-size: 16px;
    }

    .search-box button {
      background-color: #0a2a66;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    .listings {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 15px;
    }

    .card {
      background: white;
      border-radius: 8px;
      padding: 12px;
    }

    .card img {
      width: 100%;
      border-radius: 6px;
    }

    .card button {
      width: 100%;
      padding: 10px;
      margin-top: 10px;
      background-color: #0a2a66;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }

    footer {
      background-color: #0a2a66;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 25px;
    }
  </style>
</head>

<body>

<header>
  <h1>Wemert Group Realty</h1>
  <p>Affordable Homes in Orlando, FL</p>
</header>

<div class="container">

  <!-- SEARCH SECTION -->
  <div class="search-box">
    <h2>Search Affordable Homes</h2>
    <input type="number" id="price" placeholder="Maximum Price ($)">
    <input type="number" id="bedrooms" placeholder="Minimum Bedrooms">
    <button onclick="searchHomes()">Search Homes</button>
  </div>

  <!-- LISTINGS -->
  <div class="listings" id="listings"></div>

</div>

<footer>
  <p><strong>Wemert Group Realty</strong></p>
  <p>Email: jwemertgrouprealty1@gmail.com</p>
  <p>Phone: 407-435-5072</p>
</footer>

<script>
  const homes = [
    {
      price: 180000,
      bedrooms: 2,
      image: "https://via.placeholder.com/400x250",
      description: "Affordable 2 Bedroom Apartment - Orlando, FL"
    },
    {
      price: 220000,
      bedrooms: 3,
      image: "https://via.placeholder.com/400x250",
      description: "3 Bedroom Family Home - Orlando, FL"
    },
    {
      price: 260000,
      bedrooms: 4,
      image: "https://via.placeholder.com/400x250",
      description: "4 Bedroom Duplex - Great Value in Orlando"
    }
  ];

  function displayHomes(list) {
    const listings = document.getElementById("listings");
    listings.innerHTML = "";

    list.forEach(home => {
      listings.innerHTML += `
        <div class="card">
          <img src="${home.image}" alt="House">
          <p>${home.description}</p>
          <strong>$${home.price.toLocaleString()}</strong>
          <button onclick="contact()">Buy / Inquire</button>
        </div>
      `;
    });
  }

  function searchHomes() {
    const maxPrice = document.getElementById("price").value;
    const minBedrooms = document.getElementById("bedrooms").value;

    const filtered = homes.filter(home =>
      (!maxPrice || home.price <= maxPrice) &&
      (!minBedrooms || home.bedrooms >= minBedrooms)
    );

    displayHomes(filtered);
  }

  function contact() {
    alert("Thank you for your interest! We will contact you via email.");
  }

  displayHomes(homes);
</script>

</body>
</html>
