# MATLAB
MATLAB Digital Image Processing Codes
clc; clear; close all;

% ---- Read & Convert Image ----
img = imread('leaf.jpeg');
imggray = rgb2gray(img);  
[rows, cols] = size(imggray); % rows and colm calcualte

% ---- Translation Values ----
shift_rows = 20;    % vertical shift
shift_cols = 30;    % horizontal shift

translated = zeros(rows, cols); % blank screen behind image

% ---- Translation Logic ----
for r = 1:rows  % r= rows
    for c = 1:cols  % c= colms
        r_new = r + shift_rows;  % new row position
        c_new = c + shift_cols;  % new column position
        
        % check if new position is inside image
        if r_new <= rows && c_new <= cols
            translated(r_new, c_new) = imggray(r, c);
        end
    end
end

% ---- Show Images ----
figure;
subplot(1,2,1); imshow(img); title('Original Image');
subplot(1,2,2); imshow(uint8(translated)); title('Translated Image');

