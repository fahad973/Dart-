# Dart-

Finding the longest subsequence of consecutive numbers in a list:

void main() {
  List<int> nums = [2, 5, 7, 8, 9, 10, 12, 13, 14, 15, 16, 17];
  
  List<int> subseq = [];
  List<int> longestSubseq = [];

  for (int i = 0; i < nums.length - 1; i++) {
    subseq.clear();
    subseq.add(nums[i]);

    for (int j = i + 1; j < nums.length; j++) {
      if (nums[j] == subseq.last + 1) {
        subseq.add(nums[j]);
      } else {
        break;
      }
    }

    if (subseq.length > longestSubseq.length) {
      longestSubseq = List.from(subseq);
    }
  }

  print("Longest subsequence: $longestSubseq");
}


Finding the shortest distance between two cities, given their latitude and longitude coordinates:


import 'dart:math' show cos, sqrt;

void main() {
  Map<String, List<double>> cities = {
    "New York": [40.7128, -74.0060],
    "Los Angeles": [34.0522, -118.2437],
    "London": [51.5074, -0.1278],
    "Paris": [48.8566, 2.3522],
    "Sydney": [-33.8651, 151.2094],
    "Tokyo": [35.6762, 139.6503]
  };

  String startCity = "New York";
  String endCity = "Tokyo";

  double startLat = cities[startCity][0];
  double startLng = cities[startCity][1];
  double endLat = cities[endCity][0];
  double endLng = cities[endCity][1];

  double earthRadius = 6371.0; // in km

  double latDistance = toRadians(endLat - startLat);
  double lngDistance = toRadians(endLng - startLng);

  double a = pow(sin(latDistance / 2), 2) +
      cos(toRadians(startLat)) *
          cos(toRadians(endLat)) *
          pow(sin(lngDistance / 2), 2);
  double c = 2 * atan2(sqrt(a), sqrt(1 - a));

  double distance = earthRadius * c;

  print("Distance between $startCity and $endCity: ${distance.toStringAsFixed(2)} km");
}

double toRadians(double degrees) {
  return degrees * (pi / 180);
}

Sorting a list of maps by the total cost of each product:

void main() {
  List<Map<String, dynamic>> products = [
    {"name": "Apple", "price": 1.99, "quantity": 10},
    {"name": "Banana", "price": 0.99, "quantity": 20},
    {"name": "Orange", "price": 2.49, "quantity": 5},
    {"name": "Grape", "price": 3.99, "quantity": 8},
    
    
    
    
 Create a list of strings and find the longest common subsequence (substring) among all the strings in the list.
 
    void main() {
  List<String> strings = ["abcbdab", "bdcaba", "abcde"];

  String longestCommonSubseq = "";

  for (int i = 0; i < strings[0].length; i++) {
    for (int j = i + 1; j <= strings[0].length; j++) {
      String subseq = strings[0].substring(i, j);

      bool isSubseq = true;

      for (int k = 1; k < strings.length; k++) {
        if (!strings[k].contains(subseq)) {
          isSubseq = false;
          break;
        }
      }

      if (isSubseq && subseq.length > longestCommonSubseq.length) {
        longestCommonSubseq = subseq;
      }
    }
  }

  print("Longest common subsequence: $longestCommonSubseq");
}
