#include <iostream>
#include <vector>
#include <cmath>
#include <climits>

std::vector<int> findMaxNetworkQuality(std::vector<std::vector<int>>& towers, int radius) {
    int maxQuality = INT_MIN;
    std::vector<int> maxCoordinate = {INT_MAX, INT_MAX}; // Initializing with maximum possible values for lexicographical comparison
    
    for (const auto& tower : towers) {
        int x = tower[0];
        int y = tower[1];
        int quality = tower[2];
        
        int totalQuality = 0;
        for (const auto& t : towers) {
            int xt = t[0];
            int yt = t[1];
            int qt = t[2];
            
            double distance = std::sqrt((x - xt) * (x - xt) + (y - yt) * (y - yt));
            if (distance <= radius) {
                totalQuality += qt / (1 + distance);
            }
        }
        
        if (totalQuality > maxQuality || (totalQuality == maxQuality && x < maxCoordinate[0]) || 
            (totalQuality == maxQuality && x == maxCoordinate[0] && y < maxCoordinate[1])) {
            maxQuality = totalQuality;
            maxCoordinate = {x, y};
        }
    }
    
    return maxCoordinate;
}

int main() {
    int n;
    std::cout << "Enter the number of towers: ";
    std::cin >> n;
    
    std::vector<std::vector<int>> towers(n, std::vector<int>(3));
    
    std::cout << "Enter the coordinates and quality factor for each tower:\n";
    for (int i = 0; i < n; i++) {
        std::cin >> towers[i][0] >> towers[i][1] >> towers[i][2];
    }
    
    int radius;
    std::cout << "Enter the radius: ";
    std::cin >> radius;
    
    std::vector<int> result = findMaxNetworkQuality(towers, radius);
    
    std::cout << "The integral coordinate with maximum network quality: [" << result[0] << ", " << result[1] << "]\n";
    
    return 0;
}
