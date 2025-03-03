from flask import Flask, request, jsonify, send_from_directory
from flask_cors import CORS
import cv2
import numpy as np
import os

app = Flask(__name__)
CORS(app)

UPLOAD_FOLDER = 'uploads'
os.makedirs(UPLOAD_FOLDER, exist_ok=True)

@app.route('/api/outline', methods=['POST'])
def outline_image():
    if 'image' not in request.files:
        return jsonify({'error': 'No image uploaded'}), 400
    
    image_file = request.files['image']
    detail_level = int(request.form.get('detailLevel', 50))

    try:
        image_path = os.path.join(UPLOAD_FOLDER, image_file.filename)
        image_file.save(image_path)

        # Process image to outline it
        image = cv2.imread(image_path, cv2.IMREAD_COLOR)
        gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
        
        # Adjust edge detection logic for more refined details
        min_val = max(10, detail_level // 2)
        max_val = detail_level * 3
        edges = cv2.Canny(gray, threshold1=min_val, threshold2=max_val, apertureSize=3, L2gradient=True)

        # Invert colors: white background, black lines
        inverted_edges = cv2.bitwise_not(edges)

        # Convert single-channel image to 3-channel to save as a color image
        outlined_image = cv2.cvtColor(inverted_edges, cv2.COLOR_GRAY2BGR)

        outlined_image_path = os.path.join(UPLOAD_FOLDER, f"outlined_{image_file.filename}")
        cv2.imwrite(outlined_image_path, outlined_image)

        return jsonify({'outlinedImageUrl': f"http://localhost:5001/uploads/outlined_{image_file.filename}"})
    
    except Exception as e:
        return jsonify({'error': str(e)}), 500

@app.route('/uploads/<filename>')
def get_image(filename):
    return send_from_directory(UPLOAD_FOLDER, filename)

if __name__ == '__main__':
    app.run(host='localhost', port=5001)
